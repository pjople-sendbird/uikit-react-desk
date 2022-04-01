# uikit-react-desk
How to list channels for chats only and not for Desk

This is a custom application using UIKit.

## Write your Sendbird information

To try this, please change ```const.js``` file.

```
export const APP_ID = "...";
export const USER_ID = "...";
export const NICKNAME = "...";
export const ACCESS_TOKEN = "...";
```

## Listing channels

The second piece of code is to set a custom query for the list of channels.
Inside ```CustomizedApp.js``` you will see:

```
    const [queries] = useState({
        channelListQuery: {
            includeEmpty: true,
            order: 'latest_last_message',
            customTypesFilter: ['']
        },
        applicationUserListQuery: {
            limit: 100
        },
    });
```

You can define anything you want here. All the information is here: 
https://sendbird.com/docs/uikit/v1/react/guides/group-channel#4-list-of-properties

Next, apply this query to the list of channels:

```
  <SBChannelList
      queries={queries}
      onChannelSelect={(channel) => {
          if (channel && channel.url) {
              setCurrentChannelUrl(channel.url);
          }
      }}
  />
```

