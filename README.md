# Self-hosted Outline
This is a minimal, self-hostable Outline setup.
* Local file storage (exposed as local volume)
* GitLab OIDC

# Setup
## Configure a GitLab Application
1. Create a GitLab Application.
	* For User-level applications, click [here](https://gitlab.com/-/user_settings/applications).
	* For Group-level applications: Go to your Group. In the sidebar, **Settings** > **Applications**.
2. The redirect URI should look something like `https://example.com/auth/oidc.callback`.
3. The minimum scopes required are:
	* `openid`
	* `profile`
	* `email`
4. Save.

> Remember the `Application ID` and `Secret` for later.

## Running the Docker Container
1. Clone this repository.
2. `cp sample.env .env`
3. Fill `.env` with your organizations details.
4. `docker compose up -d`.

> You can use `openssl rand -hex 32` to generate random strings.

> IMPORTANT: This method grants access to **any** GitLab user. If you want to limit access, add a dummy domain under "Allowed domain" in Outline settings.

# See Also
* [Outline Documentation - Hosting Outline](https://docs.getoutline.com/s/hosting/doc/hosting-outline-nipGaCRBDu)
* [GitLab Docs - GitLab as OpenID Connect identity provider](https://docs.gitlab.com/ee/integration/openid_connect_provider.html)
