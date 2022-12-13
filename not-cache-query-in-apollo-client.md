### Not to cache Query in Apollo client

````
   const { data } = apollo_client.query<GetUnreadNotificationsCountQuery>({
        query: GetUnreadNotificationsCountDocument,
        variables: { user_id },
        errorPolicy: 'all',
        fetchPolicy: 'no-cache',<--- here if want caching then use 'network-only'
      });
 ````     
 
### Read cached data from the apollo_client cache
````
      const viewerData = apollo_client.readQuery({ query: GetViewerDocument });
````

[more info](https://www.apollographql.com/docs/react/v2/caching/cache-interaction/)
