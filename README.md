When developing a native mobile application, such as an iOS or Android application, you can choose between the following login flows: native or browser-based.

When using a browser-based login flow, the user is shown a web browser and redirected to the Auth0 login page, where they can either sign up or log in. For example, an iOS application opens a SafariViewController or Android application opens a Custom Chrome Tab.

When using a native login flow, the user signs up or enters their credentials directly into the app.

If your platform supports it, we recommend that you use a browser-based login flow where your application presents an in-application (embedded) browser for login and signup. Using an in-application browser gives your application the benefits of browser-based authentication, such as shared authentication state and security context, without disrupting the user experience by switching applications. Regardless of which option you choose, Auth0 supports either.

Single Sign-on across native applications
If you have several mobile applications (such as Google Drive, Google Docs/Sheets, YouTube, and so on), you might want to automatically log the user into all of them if they log into any one app.

If your applications use a wholly native experience, your users have to enter their credentials for each application. However, if you use a browser-based login flow you can implement Single Sign-on (SSO), reducing the number of times the user has to log in.

SSO across devices/desktops/laptops
Google is currently investing in the ability to synchronize sessions across devices called Google SmartLock. This allows users to sign in using one device or desktop/laptop computer and automatically sync their session across all of their devices. To learn more, read Sync passwords across your devices in the Google Help Center.

While SmartLock is not yet universal, using browser-based login flows allows you to take advantage of this tool.

Phishing and security issues
With a native login flow, an unauthorized party could decompile or intercept traffic to/from your application to get the Client ID and authentication URL. With this information the unauthorized party could create a rogue application, upload it to an application store, and use it to phish for usernames, passwords, and Access Tokens.

Using a browser-based flow protects you from this, since the callback URL is linked to the application through universal links (iOS) or App Links (Android). Note, however, that this is not a universally supported feature. To learn more about universal app links, read Universal Links for Developers on apple.com. To learn more about App Links, read Enable Android App Links Support.

Implementation time
Using browser-based flows reduces the implementation time required, since everything is handled by the hosted login page (including multi-factor authentication and attack protection).

By default, Lock provides the user experience, but you can customize it with your own templates written in HTML and CSS, then integrate it with auth0.js.

Automatic improvements
By relying on a Universal Login experience, you will automatically receive new features without requiring you to make any changes to your native application. For example, if Auth0 adds support for FIDO/U2F, you would not need to make any code changes to your application before you can use this functionality. To learn more about FIDO/U2F, read What is FIDO U2F? on yubico.com.

Load time and user experience
When using a native login flow, the login UI and logic is included in the application. With a browser-based login flow, the user sees some loading time as the page loads.

However, it's worth noting that the number of times a user logs in with the mobile devices is low. Once the user logs in, your application should only log them out if you revoke their access or if the user opts to log out.

Compliance with best practices
As explained in the RFC 8252 OAuth 2.0 for Native Apps, OAuth 2.0 authorization requests from native apps should only be made through external user-agents, primarily the user's browser. The specification details the security and usability reasons why this is the case.
