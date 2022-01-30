# How and When to Use Context in React with Hooks | Tania Rascia

Source: Article
Status: Unprocessed
URL: https://www.taniarascia.com/react-context-api-hooks/

![https://www.taniarascia.com/logo.png](https://www.taniarascia.com/logo.png)

---

![logo.png](How%20and%20When%20to%20Use%20Context%20in%20React%20with%20Hooks%20Ta%20094b4574437142bcbc7f6c70dd94f0e2/logo.png)

A while ago, I wrote an article about [Using Context API in React](https://www.taniarascia.com/using-context-api-in-react/). However, most of my examples on that page used Class components, `static contextType`, and `Consumer`, which is a legacy way of dealing with Context and in TYOOL 2021 we want nice, clean, functional components. I needed to use Context for something recently after quite a while, and I wanted a more succinct explanation using only modern syntax. I decided I'd write a little follow up here for a realistic use of Context.

[Context](https://reactjs.org/docs/context.html) allows you to pass data across any number of React components, regardless of nesting.

In a very small application, you might be able to get away with just using Context for most of your global data storage needs, but in a large-scale production environment, you're likely using [Redux](https://www.taniarascia.com/redux-react-guide/) for global state management. Redux still provides improved performance, improved debugging capabilities, architectural consistency, the ability to use middleware, and more. Therefore, Context is not a replacement for a proper global state management system.

Often, examples for Context will show something like a dark mode toggle, which is fine for a quick example. However, a real-life example of dark theme usage outside of a small blog or website would probably involve a user with settings they can save and persist across any session, not just temporary state in `localStorage` that gets toggled via Context. In that case, your dark mode state would be saved into Redux, since it would probably be saved as the whole currently logged-in `user` object, and require an API call to make changes.

So I'm going to provide a summary of just how to set up Context with modern React syntax, then go into an example of using Context and how it might work.

If you just want some code to copy to create, provide, and consume context, here it is:

You'll usually have one file that uses `createContext` and exports a `Provider` wrapper:

```
import React, { createContext } from 'react'

export const Context = createContext()

export const Provider = ({ children }) => {
  const [state, setState] = useState({})

  const value = {
    state,
    setState,
  }

  return <Context.Provider value={value}>{children}</Context.Provider>
}
```

Then you'll wrap whatever component needs access to the Context state with the `Provider`:

```
import React from 'react'

import { Provider } from './Context'
import { ConsumingComponent } from './ConsumingComponent'

export const Page = () => {
  return (
    <div>
      <Provider>
        <ConsumingComponent />
      </Provider>
    </div>
  )
}
```

And the consuming component can now use the `useContext` hook to access the data:

```
import React, { useContext } from 'react'

import { Context } from './Context'

export const ConsumingComponent = () => {
  const { state } = useContext(Context)

  return null
}
```

So when should you use Context, if it's not used for the same purposes as Redux? Well, in my experience, Context makes sense for something a little bit more localized and reusable. For example, you have a Dashboard widget that has controls that are common across many types of widgets. Let's say every widget receives data but can change the view between bar graph, line graph, or table view. In that case, you can create a Context Provider that sets the state of the controls and updates them, and pass them to any consumer.

You use `createContext()` to create a Context, which also creates a `Provider` and a `Consumer`, but you only need the `Provider`, which will allow any React element below it in the tree to use the Context.

```
import React, { useState, createContext } from 'react'

export const DashboardWidgetContext = createContext()

export const DashboardWidgetProvider = ({ children }) => {
  const [dataView, setDataView] = useState('table')

  const handleChangeView = value => {
    setDataViewView(value)
  }

  const value = {
    dataView,
    handleChangeView,
  }

  return <DashboardWidgetContext.Provider value={value}>{children}</DashboardWidgetContext.Provider>
}
```

Then you might have a component that handles the actions. This is a contrived example, but it would contain a `select` that lets you switch between a bar graph, line chart, or table view. Maybe it also has an "export as CSV" button, or some other actions that can apply to all the data in the widget. Now you don't have to handle the controls for each widget individually, but one time for all widgets.

Here you can see the `useContext` hook allows you to access the data from Context.

```
import React, { useContext } from 'react'

import { DashboardWidgetContext } from './DashboardWidget.context'

export const DashboardWidgetControls = ({ label }) => {
  const { dataView, handleChangeView } = useContext(DashboardWidgetContext)

  return (
    <div>
      <select value={dataView} onChange={handleChangeView}>
        <option value="bar_graph">Bar Graph</option>
        <option value="line_chart">Line Chart</option>
        <option value="table">Table</option>
      </select>
    </div>
  )
}
```

Whatever unique data you need to do on a localized level, you can do in the individual component while still having access to the outer control data. This part might be handled individually, because it might be a grouped or a stacked bar chart, or a nested table, and maybe there are a lot of tweaks that have to happen on that level.

```
import React, { useContext } from 'react'

import { DashboardWidgetContext } from './DashboardWidget.context'

export const SomeDataComponent = () => {
  const { dataView } = useContext(DashboardWidgetContext)

  switch (dataView) {
    case 'table':
      return <Table />
    case 'line_chart':
      return <LineChart />
    case 'bar_chart':
      return <BarChart />
  }
}
```

Now wherever you need the widget, you can bring in the `Provider` and the controls. I'll just put it in to a wrapper component:

```
import React from 'react'

import { DashboardWidgetProvider } from './DashboardWidget.context'
import { DashboardWidgetControls } from './WidgetControls'

export const DashboardWidget = ({ title, children }) => {
  return (
    <WidgetProvider>
      <section>
        <h2>{title}</h2>
        <WidgetControls />
        {children}
      </section>
    </WidgetProvider>
  )
}
```

```
import React from 'react';

import { DashboardWidget } from './DashboardWidget';

export const DashboardPage = () => {
  return (
    <div>
      <h1>Dashboard</h1>

      <DashboardWidget title="Distance of Planets to the Sun">
        <PlanetDistance />
      </DashboardWidgetProvider>

      <DashboardWidget title="Time Dilation and the Speed of Light">
        <SpeedOfLight />
      </DashboardWidget>
    </div>
  );
};
```

Perhaps in this case the actual data is stored in Redux because it might be used elsewhere aside from just this dashboard component, and only the controls need to be handled on a localized level. This is one example where I can see Context making a lot of sense, because passing that data around manually can start to become unintutive or there would be a lot of repetition to handle the same kind of state. I feel like it would be messy to try to handle something like this in Redux, because if you wanted multiple widgets to all be visible at once you'd need it to look like `widgets: { widget1: 'bar', widget2: 'table' }` or have a separate store for each individual widget.

I hope that was a relatively clear example of a situation in which you might use Context and the modern syntax with which to use it.