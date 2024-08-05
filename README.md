![](https://github.com/vrchatapi/vrchatapi.github.io/blob/main/static/assets/img/lang/lang_javascript_banner_1500x300.png?raw=true)

# VRChat API Library for JavaScript/TypeScript

A JavaScript/TypeScript/NodeJS client to interact with the unofficial VRChat API. Supports all REST calls specified in the [API specification](https://github.com/vrchatapi/specification).

This is a Foked Version with some Addons and Support for more Features.

## Disclaimer

This is the official response of the VRChat Team (from Tupper more specifically) on the usage of the VRChat API.

> Use of the API using applications other than the approved methods (website, VRChat application) are not officially supported. You may use the API for your own application, but keep these guidelines in mind:
> * We do not provide documentation or support for the API.
> * Do not make queries to the API more than once per 60 seconds.
> * Abuse of the API may result in account termination.
> * Access to API endpoints may break at any given time, with no warning.

As stated, this documentation was not created with the help of the official VRChat team. Therefore this documentation is not an official documentation of the VRChat API and may not be always up to date with the latest versions. If you find that a page or endpoint is not longer valid please create an issue and tell us so we can fix it.

## Getting Started

```bash
npm i vrchat-extended
```

below is an example on how to logon to the API and fetch your own user information.

```typescript
         
  const configuation = new VRChat.Configuration({
      username: "username",
      password: "password"
  });



  const axiosInstance = VRChat.VRChatHead("SOFTWARE/1.0.0.0 email@domain");
  const AuthenticationApi = new VRChat.AuthenticationApi(configuation, undefined, axiosInstance);
  const CurrentUser = await AuthenticationApi.getCurrentUser()
  
  if(!CurrentUser.data.displayName) {
    const totpCode = VRChat.GenerateTOTP();
    await AuthenticationApi.verify2FA({ code: totpCode.code });
  } 
  
  const CurrentUserObject = await AuthenticationApi.getCurrentUser();
  const currentUser = CurrentUserObject.data;
  console.log(`Logged in as: ${currentUser.displayName}`);
  

```

## Contributing

Contributions are welcome.
