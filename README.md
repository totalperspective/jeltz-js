# JeltzJS
## Crafting Fluent APIs with Vogonian Precision

> “Vogon poetry is, of course, the third worst in the Universe.
> The second worst is that of the Azgoths of Kria.
> During a recitation by their poet master Grunthos the Flatulent of his poem
> "Ode to a Small Lump of Green Putty I Found in My Armpit One Midsummer Morning,"
> four of his audience died of internal hemorrhaging,
> and the president of the Mid-Galactic Arts Nobbling Council survived only by gnawing one of his own legs off.”
>
> - Douglas Adams, The Hitchhiker's Guide to the Galaxy

Welcome to JeltzJS, 
your go-to library for crafting Fluent APIs with the precision and bureaucratic finesse of Prostetnic Vogon Jeltz himself.
Just like Vogon poetry,
our goal is to make your code as clear,
structured, and efficiently bureaucratic as possible.

### Inspired by Vogon Poetry

Vogon poetry is an art form unto itself,
albeit one of the least appreciated.
Despite its unpopularity,
we draw inspiration from the Vogons' unwavering commitment to their craft.
Just as Vogon poetry perseveres despite its critics,
so too does JeltzJS strive for perfection in the world of Fluent APIs.

## The Challenge: Dealing with Multiple APIs

In the vast galaxy of JavaScript development,
dealing with numerous internal and external APIs can be a daunting task.
Different services,
varied documentation styles,
and inconsistent interfaces create a complex web that developers must navigate.

And most of the time we're just flowing the return from one function to the argments of the next:

```javascript
// Traditional Approach
const user = db.fetchUser(userId)
if (user) {
  const isAuthed = auth.authenticateUser(user, token)
  if (!isAuthed) {
    throw new Error(`User must be authed`)
  }
  const socialMediaInfo = socials.fetchInfo(user) || {}
  // ...
}
```

This challenge calls for a solution that simplifies and unifies the interaction with these APIs.

### Fluent APIs: A Solution to Complexity

Fluent APIs offer a solution to the complexity of working with many APIs.
They allow you to create a unified and expressive interface for various services,
making your code more readable and maintainable.

```javascript
// Using Fluent APIs
const socialMediaInfo = fluentUser(userId)
  .fetchUserFromDatabase(db)
  .authenticateUser(token)
  .fetchSocialMediaInfo() || {}
```

## Defining the JeltzJS API

Now,
with JeltzJS at your disposal,
you can tame the unruly APIs of the galaxy with Vogonian precision.

### Step 1: Define JeltzJS API

JeltzJS simplifies the creation of Fluent APIs for handling multiple API calls.
It allows you to define and compose APIs using a spoecificaton,
providing a structured and efficient way to interact with different services.

```javascript
import jeltz from 'jeltz'
// userAPI.jeltz.js
export default {
  fetchUserFromDatabase: {
    requires: ['string'],
    returns: ['user', null],
    do: (userId, db) => db.fetchUser(userId),
  },
  authenticateUser: {
    requires: ['user'],
    returns: ['authedUser', false],
    do: (user, token) => auth.authenticateUser(user, token) && user,
    cantDo: () => jeltz.done(null)
  },
  fetchSocialMediaInfo: {
    requires: ['authedUser'],
    returns: ['socialMediaData'],
    do: (user) => socials.fetchInfo(user),
    cantDo: () => throw new Error(`User must be authed`),
  },
  orVal: {
    do: (val, orVal) => val || orVal
  }
}
```

### Step 2: Use JeltzJS

Now that you have defined your Fluent API using JeltzJS,
it's time to utilize it to streamline the interaction with like we saw in the previous example.

```javascript
import jeltz from 'jeltz'
import userAPI from './userAPI.jeltz.js'

const fluent = jeltz.build(userApi)
const fluentUser = fluent
  .fetchUserFromDatabase(userId)
  .authenticateUser(token)
  .fetchSocialMediaInfo()
  .orVal({})
  .execute();
```

### Contributing

If you wish to contribute to JeltzJS and uphold the Vogon spirit, please review our [Contribution Guidelines](CONTRIBUTING.md).
We welcome your finely tuned outrage in the form of bug reports, feature requests, or even poetry (Vogon-approved only).

### License

JeltzJS is licensed under the [MIT License](LICENSE.md), ensuring it can be shared and adapted across the galaxy.

### Vogon Poetry Warning

Before diving into JeltzJS, remember the words of The Guide:

> "Vogon poetry is, of course, the third worst in the Universe."

While our library strives for precision, we promise the coding experience is far more pleasant than a recitation of Vogon verse.

Now, let the bureaucratic elegance of JeltzJS guide you through the intricacies of crafting Fluent APIs in JavaScript.
May your code be as finely judged as the outrage of a Vogon bureaucrat!
