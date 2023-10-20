# Create a chat dApp using Solidity and ReactJS

## Introduction
The dApp will allow users to connect with other people and chat with them. We will develop our smart contract using Solidity. We will have a basic, easy-to-use UI developed using ReactJS. So, let us begin!

## Requirements

* [Node.js](https://nodejs.org/en/download/releases/) v10.18.0+
* [Metamask extension](https://metamask.io/download.html) on your browser

## Implementing the smart contract

Our chat dApp needs the basic functionality allowing users to connect with and share messages with friends. To accomplish this, we will write the functions responsible for creating an account, adding friends and sending messages.

### Account creation

We will define 3 functions :

* The `checkUserExists(pubkey)` function is used to check if a user is registered with our application or not. It will help make sure duplicate users are not created and it will also be called from other functions to check their existence.

* The `createAccount(username)` function registers a new user on the platform with the provided username.

* The `getUsername(pubkey)` function will return the username of the given user if it exists.

### Adding friends

Here also we will define 3 functions :

* The `checkAlreadyFriends(pubkey1, pubkey2)` function checks whether two users are already friends with each other or not. This is needed to prevent duplicate channel between the same parties and will also be used to prevent a user from sending messages to other users unless they are friends.

* The `addFriend(pubkey, name)` function mark the two users as friend if they both are registered on the platform and are already not friends with each other.

* The `getMyFriendList()` function will return an array of friends of the given user.

### Messaging

The final part of the Solidity contract will enable the exchange of messages between users. We will divide the task into two functions `sendMessage()` and `readMessage()`.

* The `sendMessage()` function allows a user to send messages to another registered user (friend). This is done with `checkUserExists(pubkey)` and `checkAlreadyFriends(pubkey1, pubkey2)`.

* The `readMessage()` function returns the chat history that has happened between the two users so far.

### User Data Collections

We will have three types of user-defined data :

* `user` will have the properties `name` which stores the username, and `friendList` which is an array of other users.

* `friend` will have the properties `pubkey` which is the friends' public address, and `name` which the user would like to refer them as.

* `message` has three properties: `sender`, `timestamp` and `msg`, which is short for "message".

We would maintain 2 collections in our database:

* `userList` where all the users on the platform are mapped with their public address.

* `allMessages` stores the messages. As Solidity does not allow user-defined keys in a mapping, we can instead hash the public keys of the two users. This value can then be stored in the mapping.

## Deploying the smart contract

install dependencies.

Now its time to run our React app frontend. Use the following command inside the project root directory:

```bash
npm start
```


## About the Author(s)

Dheeraj kaushik
