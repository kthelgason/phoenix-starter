![](https://raw.githubusercontent.com/mjcloutier/mjcloutier.github.io/master/banner.png)
Phoenix Starter
=======================

A boilerplate for **Phoenix Framework** web applications. Forked from [mjcloutier](https://github.com/sahat/hackathon-starter)
but modified to have a smaller scope and more targeted at my own use case.

Table of Contents
-----------------

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Obtaining API Keys](#obtaining-api-keys)
- [List of Packages](#list-of-packages)
- [License](#license)

Features
--------

- [x] **Local Authentication** using Email and Password.
- [x] **OAuth 2.0 Authentication** via Facebook or Google.
- [x] **OAuth 1.0a Authentication** via Twitter.
- [x] Flash notifications.
- [x] MVC Project Structure.
- [x] Sass stylesheets (auto-compiled via Brunch).
- [x] Bootstrap 4.
- [x] CSRF protection.

- [ ] **User Account Management**
  - [ ] Avatar Image Upload with (Gravatar/Identicon fallback).
    - [ ] Upload Avatar via link or File Upload.
    - [ ] Delete Avatar.
    - [ ] Edit Avatar.
  - [ ] Profile Details.
  - [ ] Change Password.
  - [ ] Password Confirmation.
  - [ ] Forgot Password.
  - [ ] Reset Password.
  - [x] Link multiple OAuth strategies to one account.
  - [ ] Delete strategies linked to an account.
  - [ ] Delete Account.

- [x] **Admin Account Management (via ExAdmin)**
  - [x] Manage Users.
  - [ ] Manage Application Settings.

- [ ] **Mailers**
  - [ ] Reset Password.
  - [ ] Confirm Password.
  - [ ] Welcome.
  - [ ] Delete Account.


Prerequisites
-------------

- [Postgresql](http://www.postgresql.org/)
- [Erlang](https://www.erlang.org/)
- [Elixir](http://elixir-lang.org/)
- [Phoenix](http://www.phoenixframework.org/)
- [Foreman](http://ddollar.github.io/foreman/)

Getting Started
---------------

The easiest way to get started is to clone the repository:

```bash
# Get the latest snapshot
git clone --depth=1 https://github.com/iNeedThis/phoenix-starter.git myproject

# Change directory
cd myproject

# Create an .envrc from the .envrc.example provided and fill in the blanks.
cp .envrc.example .envrc

# Get phoenix dependencies & Install NPM dependencies
mix deps.get && npm install

# Create Database & migrate
source .envrc && mix ecto.setup

# Run Project
./start
```

Obtaining API Keys
------------------

To use any of the included APIs or OAuth authentication methods, you will need
to obtain appropriate credentials: Client ID, Client Secret, API Key, or
Username & Password. You will need to go through each provider to generate new
credentials.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/1000px-Google_2015_logo.svg.png" width="200">
- Visit [Google Cloud Console](https://cloud.google.com/console/project)
- Click on the **Create Project** button
- Enter *Project Name*, then click on **Create** button
- Then click on *APIs & auth* in the sidebar and select *API* tab
- Click on **Google+ API** under *Social APIs*, then click **Enable API**
- Next, under *APIs & auth* in the sidebar click on *Credentials* tab
- Click on **Create new Client ID** button
- Select *Web Application* and click on **Configure Consent Screen**
- Fill out the required fields then click on **Save**
- In the *Create Client ID* modal dialog:
 - **Application Type**: Web Application
 - **Authorized Javascript origins**: http://localhost:3000
 - **Authorized redirect URI**: http://localhost:3000/auth/google/callback
- Click on **Create Client ID** button
- Copy and paste *Client ID* and *Client secret* keys into `.env`

**Note:** When you ready to deploy to production don't forget to
add your new url to *Authorized Javascript origins* and *Authorized redirect URI*,
e.g. `http://my-awesome-app.herokuapp.com` and
`http://my-awesome-app.herokuapp.com/auth/google/callback` respectively.
The same goes for other providers.

<hr>

<img src="http://www.doit.ba/img/facebook.jpg" width="200">
- Visit [Facebook Developers](https://developers.facebook.com/)
- Click **My Apps**, then select **Add a New App* from the dropdown menu
- Select **Website** platform and enter a new name for your app
- Click on the **Create New Facebook App ID** button
- Choose a **Category** that best describes your app
- Click on **Create App ID** button
- In the upper right corner click on **Skip Quick Star**
- Copy and paste *App ID* and *App Secret* keys into `.env`
 - **Note:** *App ID* is **clientID**, *App Secret* is **clientSecret**
- Click on the *Settings* tab in the left nav, then click on **+ Add Platform**
- Select **Website**
- Enter `http://localhost:3000` under *Site URL*

**Note:** After a successful sign in with Facebook, a user will be redirected back to home page with appended hash `#_=_` in the URL. It is *not* a bug. See this [Stack Overflow](https://stackoverflow.com/questions/7131909/facebook-callback-appends-to-return-url) discussion for ways to handle it.

<hr>

<img src="https://github.global.ssl.fastly.net/images/modules/logos_page/GitHub-Logo.png" width="200">
- Go to [Account Settings](https://github.com/settings/profile)
- Select **Applications** from the sidebar
- Then inside **Developer applications** click on **Register new application**
- Enter *Application Name* and *Homepage URL*
- For *Authorization Callback URL*: http://localhost:3000/auth/github/callback
- Click **Register application**
- Now copy and paste *Client ID* and *Client Secret* keys into `.env` file

<hr>

<img src="https://g.twimg.com/ios_homescreen_icon.png" width="90">
- Sign in at [https://apps.twitter.com/](https://apps.twitter.com/)
- Click **Create a new application**
- Enter your application name, website and description
- For **Callback URL**: http://127.0.0.1:3000/auth/twitter/callback
- Go to **Settings** tab
- Under *Application Type* select **Read and Write** access
- Check the box **Allow this application to be used to Sign in with Twitter**
- Click **Update this Twitter's applications settings**
- Copy and paste *Consumer Key* and *Consumer Secret* keys into `.env` file

<hr>

<img src="http://iandouglas.com/presentations/pyconca2012/logos/sendgrid_logo.png" width="200">
- Go to https://sendgrid.com/user/signup
- Sign up and **confirm** your account via the *activation email*
- Then enter your SendGrid *Username* and *Password* into `.env` file

<hr>

<img src="https://raw.github.com/mailgun/media/master/Mailgun_Primary.png" width="200">
- Go to http://www.mailgun.com
- Sign up and add your *Domain Name*
- From the domain overview, copy and paste the default SMTP *Login* and *Password* into `.env` file

<hr>

<img src="http://cdn.appstorm.net/web.appstorm.net/web/files/2013/12/mandrill-logo.png" width="100">
- Go to http://mandrill.com
- Sign up and add your *Domain Name*
- From the dashboard, click on *Get SMTP credentials*
- Copy and paste the default SMTP *Login* and *Password* into `.env` file

List of Packages
----------------

| Package                         | Description                                                           |
| ------------------------------- | --------------------------------------------------------------------- |
| phoenix                         | Productive. Reliable. Fast. A productive web framework.               |
| phoenix_ecto                    | Integration between Phoenix & Ecto.                                   |
| phoenix_html                    | Phoenix.HTML functions for working with HTML strings and templates.   |
| phoenix_live_reload             | Provides live-reload functionality for Phoenix.                       |
| cowboy                          | Small, fast, modular HTTP server written in Erlang.                   |
| guardian                        | Elixir Authentication framework.                                      |
| guardian_db                     | DB tracking for token validity.                                       |
| ueberauth                       | An Elixir Authentication System for Plug-based Web Applications.      |
| ueberauth_identity              | An Ueberauth strategy for basic username/password.                    |
| ueberauth_github                | An Ueberauth strategy for Github authentication.                      |
| ueberauth_slack                 | An Ueberauth strategy for Slack authentication.                       |
| ueberauth_google                | An Ueberauth strategy for Google authentication.                      |
| ueberauth_facebook              | An Ueberauth strategy for Facebook authentication.                    |
| ueberauth_twitter               | An Ueberauth strategy for Twitter authentication.                     |
| ueberauth_fitbit                | An Ueberauth strategy for Fitbit authentication.                      |
| comeonin                        | Password hashing (bcrypt, pbkdf2_sha512) library for Elixir.          |
| ex_admin                        | ExAdmin is an auto administration package for the Phoenix Framework   |

License
-------

The MIT License (MIT)

Copyright (c) 2017 Kári Tristan Helgason

Copyright (c) 2016 Michael Cloutier

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
