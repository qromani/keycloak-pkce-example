# Keycloak + PKCE example

## How to create a PKCE client on Keycloack
1. Create a client
2. Set `Access Type` to `public`
3. Set `Standard Flow Enabled` to `ON`
4. Set `Valid Redirect URIs` to URL of your application, for example `http://localhost:3030/*`, here you can use wildcard, this address must be the same that the application will use as callback after user signin on keycloak login page.
5. Set `Base URL` for some public accesss of your application, it will be used in case of to cancel authentication then Keycloak will recirect user for this URL
6. In `Advanced Settings > Proof Key for Code Exchange Code Challenge Method` select `S256`
7. Save the configuration!

## How to configurate Refresh Token Rotation (to prevents replay attack)
1. Go to `Realm Settings` in left menu
2. Turn on the `Revoke Refresh Token` configuration
3. A new option will appear below with the name `Refresh Token Max Reuse`, if you left the value as `0`, it will allow that the `refresh_token` can just refresh the `access_token` once. So you can configure how many times that can occur by setting another value to it. 
4. When the max of reuse is reached the Keycloak will invalidate all refresh tokens.