# Complete Guide: Setting up the Gmail OAuth API

This document provides a comprehensive step-by-step guide to setting up Google Cloud OAuth credentials and generating a Refresh Token to send emails programmatically via your Gmail account.

---

## Step 1: Create a Google Cloud Project
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Click the project dropdown at the top of the page and select **New Project**.
3. Give your project a clear name and click **Create**.
4. Ensure your newly created project is selected from the top dropdown.

---

## Step 2: Enable the Gmail API
1. Navigate to **APIs & Services** > **Enabled APIs & Services**.
2. Click the **+ Enable APIs and Services** button at the top.
3. Search for **Gmail API**, click on it, and click **Enable**.

---

## Step 3: Configure the OAuth Consent Screen & Test Users
1. Go to **APIs & Services** > **OAuth consent screen**.
2. Choose **External** (or Internal if using Google Workspace) and click **Create**.
3. Fill out the required basic information:
   * **App name**: Your project's name.
   * **User support email**: Your email address.
   * **Developer contact information**: Your email address.
4. Click **Save and Continue** through the subsequent screens.
5. Scroll down to the **Test users** section, click **Add Users**, and add your own Gmail address. Click **Save**.

---

## Step 4: Generate OAuth Client Credentials
1. Go to **APIs & Services** > **Credentials**.
2. Click **Create Credentials** at the top and select **OAuth client ID**.
3. Set the **Application type** to **Web application** (or Desktop app).
4. Give your client a name.
5. Under **Authorized redirect URIs**, add the exact URI:
   `https://developers.google.com/oauthplayground`
6. Click **Create** and securely copy your **Client ID** and **Client Secret**.

---

## Step 5: Generate the Refresh Token via OAuth Playground
1. Open the [Google OAuth 2.0 Playground](https://developers.google.com/oauthplayground/).
2. Click the gear icon (OAuth 2.0 configuration) in the top-right corner.
3. Check the box for **"Use your own OAuth credentials"**.
4. Paste your **Client ID** and **Client Secret**, then close the settings panel.
5. In the left-hand panel, expand **Gmail API v1** and check the permission scope:
   `https://www.googleapis.com/auth/gmail.send`
6. Click **Authorize APIs** and log in using your test Gmail account, granting permissions.
7. Click **Exchange authorization code for tokens**.
8. Copy and save your **Refresh Token** from the response panel.

---

## Important Limits & Constraints
* **Daily Sending Limit:** Free consumer Gmail accounts are limited to **500 emails per rolling 24-hour period**.
* **Rate Limiting:** Avoid firing all email requests simultaneously. Introduce small delays or use a queue to prevent getting blocked by Google's automated rate limits (`429 Too Many Requests`).