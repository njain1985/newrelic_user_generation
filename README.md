# Manage Users

## Description

These scripts add users to (or remove them from) a New Relic account based on a list of email addresses. (Thanks to [sdelight](https://source.datanerd.us/sdelight) for his suggestion to call the backing APIs directly, rather than using Selenium to drive a browser.)

## Required Software

- [Node.js and npm](https://nodejs.org/en/)

## Installation

1. Clone this repository to your computer. 
2. To install the application’s dependencies, open a Terminal window and execute `$ npm install`.

## Usage

### Adding users to an account

1. Create a CSV file containing a list of users to add, one user per line, in the format: `Full Name,email`
2. Edit `addUsers.js` and set the following parameters: 

    - `accountId`: The New Relic account ID to which you wish to add users
    - `login_service_tokens`: Your auth tokens, copied from a browser in which you have logged into your account. (In Google Chrome, you may obtain these tokens by visiting `chrome://settings/cookies/detail?site=newrelic.com` and copying the value of the `login_service_login_newrelic_com_tokens` cookie.)
    - `inputFile`: Path to CSV file containing email addresses to add
    - _Optional_: This script adds users as `admin`. To add them as a different user type (`user` or `restricted`), change the value of the `userLevel` variable.

3. To run the script, open a Terminal window and execute `node addUsers.js`.

You may run the script more than once. If you try to add a user who already has access to the account, New Relic will return a message to that effect and the script will continue with the next address in the file.

### Deleting all users from an account

1. Edit `deleteUsers.js` and set the following parameters: 

    - `accountId`: The New Relic account ID to which you wish to add users
    - `login_service_tokens`: Your auth tokens, copied from a browser on which you have logged into your account. In Google Chrome, you may obtain these tokens by visiting `chrome://settings/cookies/detail?site=newrelic.com` and copying the value of the `login_service_login_newrelic_com_tokens` cookie

2. _Optional_: To keep certain users in the account (such as Relics who frequently use the account), add their email addresses to the `emailsToKeep` array.
3. To run the script, open a Terminal window and execute `node deleteUsers.js`.
