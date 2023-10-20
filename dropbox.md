To interact with the Dropbox API, you'll first need to obtain an access token. Here's a step-by-step guide to get you started:

1. **Create a Dropbox Account**:
   We strongly recommend creating a new separate account that will be used only for this project. In case the OAuth token is compromised by someone they may receive sensitive information and they can act on your behalf. So it is important to create a separate account that will be used only for development purposes. Once you have an account, sign up for a Dropbox account at [Dropbox.com](https://www.dropbox.com/).

2. **Create an App**:
    - Visit the [Dropbox Developers App Console](https://www.dropbox.com/developers/apps).
    - Click the `Create App` button.
    - Choose the type of access you need:
        - **Scoped access** (recommended): Allows you to specify fine-grained permissions.
        - **Full dropbox**: Access to all files and folders in the Dropbox.
    - Choose the type of data access (App folder or Full dropbox).
    - Enter a name for your app. This should be unique.
    - Click the `Create App` button.

3. **Get the OAuth2 Token**:
   There are several ways to authenticate with the Dropbox API. The easiest method for development/testing is to generate an OAuth2 token directly from the App Console:
    - In your app's page on the App Console, find the `OAuth 2` section.
    - Under `Generated access token`, click the `Generate` button.
    - This will provide you with a token. **Copy this token and keep it secure**. Anyone with this token can access the Dropbox account in the manner defined by your app's permissions.

4. **Use the Token**:
   Once you have your token, you can use it to make authorized API requests to Dropbox. For example, in a typical HTTP request, you would include it in the header as:
   ```
   Authorization: Bearer YOUR_ACCESS_TOKEN
   ```

5. **Important Considerations**:
    - The token you generate from the App Console is long-lived. However, in a real-world application, you'd typically use OAuth2 to have users authenticate and grant your app permissions, and this would involve redirecting users to a Dropbox authentication page.
    - Always keep access tokens secure. Exposing an access token can lead to unauthorized access to the associated Dropbox account.
    - Do not push the access token to the GitHub. Once you push secured data it is considered as compromised.
    - If you're building an app for broader use (i.e., not just for personal use/testing), you'll need to implement a full OAuth2 flow, which is more involved than the steps outlined here. This ensures each user authorizes your app individually.

Remember to refer to the [Dropbox API documentation](https://www.dropbox.com/developers/documentation/http/documentation) for detailed information on endpoints, functionalities, and best practices.

HINTs:
- Check the https://content.dropboxapi.com/2/files/upload endpoint for file uploading
- Once you change the permissions (scopes) you need to regenerate token or te-authorize: if you generated an OAuth token directly from the App Console for testing, you'll need to generate a new token after updating the scopes. The new token will have the required permissions.
