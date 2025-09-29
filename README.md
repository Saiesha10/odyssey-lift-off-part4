# Odyssey Lift-off IV: Mutations

### 1. **Mutation**

* Mutations allow clients to **modify data** on the server, such as creating, updating, or deleting records.
* Unlike queries that fetch data, mutations are used for **data-changing operations**.

### 2. **Adding a Mutation to the Schema**

* Define a `Mutation` type in the schema to specify the operations available for data modification.
* Example:

  ```graphql
  type Mutation {
    incrementTrackViews(id: ID!): Track
  }
  ```
* This mutation increments the view count of a specific track identified by its `id`.

### 3. **Updating the Data Source**

* Extend the existing data source (e.g., `TrackAPI`) to handle the mutation logic.
* Implement a method like `incrementTrackViews(id)` that performs the desired operation on the data.

### 4. **Writing the Mutation Resolver**

* In the resolver, handle the mutation by calling the appropriate method from the data source.
* Example:

  ```javascript
  incrementTrackViews: (_, { id }, { dataSources }) => {
    return dataSources.trackAPI.incrementTrackViews(id);
  }
  ```
* This resolver calls the `incrementTrackViews` method from the `TrackAPI` data source.

### 5. **Handling Errors in Mutations**

* Use `try...catch` blocks to handle potential errors during mutation execution.
* Return meaningful error messages to the client to indicate what went wrong.

### 6. **Testing Mutations in the Apollo Explorer**

* Use the Apollo Sandbox Explorer to test mutations interactively.
* Example mutation:

  ```graphql
  mutation IncrementTrackViews($id: ID!) {
    incrementTrackViews(id: $id) {
      id
      numberOfViews
    }
  }
  ```
* Provide variables in the Explorer to test the mutation with different inputs.

### 7. **Using `useMutation` Hook in Apollo Client**

* On the client side, use the `useMutation` hook from Apollo Client to send mutation requests.
* Example:

  ```javascript
  const [incrementTrackViews] = useMutation(INCREMENT_TRACK_VIEWS);
  ```
* Trigger the mutation in response to user actions, such as clicking a button.


