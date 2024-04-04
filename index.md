![Screenshot](doc/Screenshot%202024-04-02%20at%2011.01.36%20AM.png)

# Digits

Digits is a Meteor application that illustrates: 

A simple website that allows users to register and save their business contacts. 
Allowing the user to save each contacts: name, address, and phone number. As well as dotting down specific notes on each person if needed.

## Installation

First, [install Meteor](https://www.meteor.com/install).

Second, go to [https://github.com/Kyj1n/digits/tree/cleanup](https://github.com/ics-software-engineering/meteor-application-template-react), and click the "Use this template" button. Complete the dialog box to create a new repository that you own that is initialized with this template's files.

Third, go to your newly created repository, and click the "Clone or download" button to download your new GitHub repo to your local file system.  Using [GitHub Desktop](https://desktop.github.com/) is a great choice if you use MacOS or Windows.

Fourth, cd into the app/ directory of your local copy of the repo, and install third party libraries with:

```
$ meteor npm install
```

## Running the system

Once the libraries are installed, you can run the application by invoking the "start" script in the [package.json file](https://github.com/ics-software-engineering/meteor-application-template-react/blob/master/app/package.json):

```
$ meteor npm run start
```

The first time you run the app, it will create some default users and data. Here is the output:

```
 meteor npm run start 

> meteor-application-template-react@ start /Users/carletonmoore/GitHub/ICS314/meteor-application-template-react/app
> meteor --no-release-check --exclude-archs web.browser.legacy,web.cordova --settings ../config/settings.development.json

[[[[[ ~/GitHub/ICS314/meteor-application-template-react/app ]]]]]

=> Started proxy.                             
=> Started HMR server.                        
=> Started MongoDB.                           
I20220529-12:09:18.384(-10)? Creating the default user(s)
I20220529-12:09:18.389(-10)?   Creating user admin@foo.com.
I20220529-12:09:18.453(-10)?   Creating user john@foo.com.
I20220529-12:09:18.515(-10)? Creating default data.
I20220529-12:09:18.515(-10)?   Adding: Basket (john@foo.com)
I20220529-12:09:18.599(-10)?   Adding: Bicycle (john@foo.com)
I20220529-12:09:18.600(-10)?   Adding: Banana (admin@foo.com)
I20220529-12:09:18.601(-10)?   Adding: Boogie Board (admin@foo.com)
I20220529-12:09:18.773(-10)? Monti APM: completed instrumenting the app
=> Started your app.

=> App running at: http://localhost:3000/
```

Periodically, you might see `Error starting Mongo (2 tries left): Cannot run replSetReconfig because the node is currently updating its configuration` after the `=> Started HMR server.`. It doesn't seem to be a problem since the MongoDB does start.

### Viewing the running app

If all goes well, the template application will appear at [http://localhost:3000](http://localhost:3000).  You can login using the credentials in [settings.development.json](https://github.com/ics-software-engineering/meteor-application-template-react/blob/main/config/settings.development.json), or else register a new account.

### ESLint

You can verify that the code obeys our coding standards by running ESLint over the code in the imports/ directory with:

```
meteor npm run lint
```

### Landing page

When you retrieve the app at http://localhost:3000, this is what should be displayed:

![Screenshot](doc/Screenshot%202024-04-02%20at%2011.01.36%20AM.png)

In this screenshot I am currenlty logged in as an admin but usually the next step is to use the Login menu to either Login to an existing account or register a new account.

#### Login page

Clicking on the Login link, then on the Sign In menu item displays this page:

![Screenshot 2024-04-03 at 10.17.28 PM.png](doc%2FScreenshot%202024-04-03%20at%2010.17.28%20PM.png)


#### Register page

Alternatively, clicking on the Login link, then on the Sign Up menu item displays this page:

![Screenshot 2024-04-03 at 10.20.10 PM.png](doc%2FScreenshot%202024-04-03%20at%2010.20.10%20PM.png)


#### Landing (after Login) page, non-Admin user

Once you log in (either to an existing account or by creating a new one), the navbar changes as follows:

![Screenshot 2024-04-03 at 10.20.50 PM.png](doc%2FScreenshot%202024-04-03%20at%2010.20.50%20PM.png)

You can now add new Contacts, and list the contacts you have created. Note you cannot see any Stuff created by other users. In our landing page we also have an Admin page as we are logged in as an admin account.

#### Add Contact page

After logging in, here is the page that allows you to add new contacts:

![Screenshot 2024-04-03 at 10.23.32 PM.png](doc%2FScreenshot%202024-04-03%20at%2010.23.32%20PM.png)

#### List Stuff page

After logging in, here is the page that allows you to list all the contacts you have created. You can also edit if needed.:

![Screenshot 2024-04-03 at 10.24.08 PM.png](doc%2FScreenshot%202024-04-03%20at%2010.24.08%20PM.png)

You click the "Edit" link to go to the Edit Stuff page, shown next.

#### Edit contact page

After clicking on the "Edit" link associated with an item, this page displays that allows you to change and save an edit to a specific contact:

![Screenshot 2024-04-03 at 10.24.42 PM.png](doc%2FScreenshot%202024-04-03%20at%2010.24.42%20PM.png)


#### Admin page (list all users stuff)

To provide a simple example of a "special power" for Admin users, the Admin page lists all of the contacts by all of the users:

### CSS

The application uses the [React implementation of Bootstrap 5](https://react-bootstrap.github.io/). You can adjust the theme by editing the `app/client/style.css` file. To change the theme override the Bootstrap 5 CSS variables.

```css
/* Use Open Sans as the default sans serif font. */
@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,400,500,700|Source+Code+Pro:300,400,500,700");

/* Set up some CSS variables to theme the application. */
:root {
  --matr-navbar-bg: darkblue;
  --matr-navbar-bg-rgb: 0, 0, 139;
  --matr-navbar-text-color: white;
  --matr-navbar-highlight-text: khaki;
}

/* Change bootstrap variable values.
 See https://getbootstrap.com/docs/5.2/customize/css-variables/
 */
body {
  --bs-dark: var(--matr-navbar-bg);
  --bs-dark-rgb: var(--matr-navbar-bg-rgb);
  background: fixed center url("images/vibrant-multicolor-beautiful-sky-cloud-copy-space-background_176697-1603.avif");
  background-size: cover;
}

body .navbar {
  --bs-navbar-active-color: var(--matr-navbar-highlight-text);
  --bs-navbar-brand-color: var(--matr-navbar-text-color);
  --bs-navbar-brand-hover-color: var(--matr-navbar-highlight-text);
  --bs-navbar-color: var(--matr-navbar-text-color);
  --bs-navbar-hover-color: var(--matr-navbar-highlight-text);
}

.bg-dark a.dropdown-item {
  color: var(--matr-navbar-bg);
}


/* Set the alert background on the signin and signup pages. */
#signin-page .alert-light, #signup-page .alert-light {
  --bs-alert-bg: var(--matr-navbar-bg);
}

/* Define custom styles */
.gray-background {
  background-color: var(--matr-navbar-bg);
  color: var(--bs-dark);
  padding-top: 10px;
  padding-bottom: 20px;
}

footer, footer a {
  color: var(--matr-navbar-text-color);
}

```

