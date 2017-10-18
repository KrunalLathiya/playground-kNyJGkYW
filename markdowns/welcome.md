# Angular Router Tutorial

The Angular CLI is a command line interface tool that can create a project, add files, and perform a variety of ongoing development tasks such as testing, bundling, and deployment. For Single Page Application, Routing is the one and only tool or we can say module to navigate the pages to pages. So, let us get started Angular 4 Router Tutorial or just Angular Router Tutorial.

The source code for this template is on [GitHub](https://github.com/KrunalLathiya/playground-kNyJGkYW), please feel free to come up with proposals to improve it.

# Step 1: Install The Angular Project.

Install Angular CLI globally on your system by typing the following command.
```
npm install -g @angular/cli
```

Now, create one project called <b>ngRouter</b>.
```
ng new ngRouter
```

# Step 2: Make three components for the application.

Create one directory inside <b>src  >>  app</b> folder called components.

Next, make three components by typing the following command.
```javascript
ng g c home
ng g c about
ng g c dashboard
```
It creates a separate folder inside <b>src  >>  app</b> directory, we need to move all these three folders inside components folder for better project structure.

So, our <b>app.module.ts</b> file looks like this.

```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { RouterModule } from '@angular/router';

import { AppComponent } from './app.component';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';
import { DashboardComponent } from './dashboard/dashboard.component';

@NgModule({
  declarations: [
    AppComponent,
    HomeComponent,
    AboutComponent,
    DashboardComponent
  ],
  imports: [
    BrowserModule, RouterModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

# Step 3: Routing and Navigation.
The <b>Angular Router</b> enables navigation from one view to the next as users perform application tasks.

First, we need to import the routing modules inside our <b>app.module.ts</b> file.

```javascript
// app.module.ts

import { RouterModule } from '@angular/router';

imports: [
    BrowserModule, RouterModule
],
```

## Configuration

When you have created the components, it’s by default path is different and now we have moved the components, so now its path is different. So, first, we need to change that path in <b>app.module.ts</b> file.

```javascript
// app.module.ts

import { HomeComponent } from './components/home/home.component';
import { AboutComponent } from './components/about/about.component';
import { DashboardComponent } from './components/dashboard/dashboard.component';
```

Okay, now we need to configure the routes. So make one file inside app directory called <b>routerConfig.ts</b> file.

Write the following code in it.

```javascript
// routerConfig.ts

import { Routes } from '@angular/router';
import { HomeComponent } from './components/home/home.component';
import { AboutComponent } from './components/about/about.component';
import { DashboardComponent } from './components/dashboard/dashboard.component';

const appRoutes: Routes = [
  { path: 'home', 
    component: HomeComponent 
  },
  {
    path: 'about',
    component: AboutComponent
  },
  { path: 'dashboard',
    component: DashboardComponent
  }
];
export default appRoutes;
```
We have defined one array and inside that array, we have registered the different routes with their components. Finally, we have exported it.

Now, import this object inside <b>app.module.ts</b> and register the module.

```javascript
// app.module.ts

import appRoutes from './routerConfig';

imports: [
    BrowserModule,
    RouterModule.forRoot(appRoutes)
],
```

# Step 4: Define the Router outlet.

In the <b>app.component.html</b> file, write the following code.

```
<!-- app.component.html  -->

<div style="text-align:center">
  <h1>
    Welcome to {{title}}!!
  </h1>
  <nav>
    <a routerLink="home" routerLinkActive="active">Home</a>
    <a routerLink="about">About</a>
    <a routerLink="dashboard">Dashboard</a>
  </nav>
  <router-outlet></router-outlet>
</div>
```
Now, we have already changed the title inside <b>app.component.ts</b> file.

```javascript
// app.component.ts

title = 'Angular Router Tutorial';
```
Start the app by the following command.

```
ng serve --open
```
After webpack compiles successfully, we can see the following page at the [localhost](http://localhost:4200/home)

@[Angular Router Tutorial]({"stubs": ["src/app/app.module.ts", "src/app/app.component.ts", "src/app/app.component.html", "src/app/routerConfig.ts", "src/app/components/about/about.component.html", "src/app/components/home/home.component.html", "src/app/components/dashboard/dashboard.component.html"], "command": "./run.sh"})