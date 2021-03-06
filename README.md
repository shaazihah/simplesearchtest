# SimpleSearchTest

Welcome! Congratulations on making our shortlist! Below you will find a task that will put your skills to the test. Good luck.


## `ClientApp` built with

* [Angular2]() - RC.4 **NOTE!!** If you go looking at the angular2 docs, remember that they will reflect the latest version of angular2, at the time of writing is RC.5.
* [angular-cli](https://github.com/angular/angular-cli) - version 1.0.0-beta.10
* SASS

##### The following steps need to be taken in order to get setup:

1. `git clone <path to your repo of test>`
2. `node` version `4.2.2` (updating this is dependent on your OS)
3. `npm` version `3.10.3` (you can usually run `npm install npm@3.10.3 -g` to update, might need to be run as `sudo` on ubuntu or mac)
4. run `npm install typings -g` (if ubuntu or mac, normally needs to be run as `sudo`)
5. run `npm install angular-cli@1.0.0-beta.10 -g` (if ubuntu or mac, normally needs to be run as `sudo`)
6. run `npm install` -> this will download and install all the packages required to build the Angular2 `ClientApp` (Don't run this `sudo`, you should not need to)
7. it should automatically run this, but in-case it doesn't, run `typings install`
8. MEGA PRO TIP: If you already have other versions of Node, NPM, typings or angular-cli installed, use Docker to instantiate a clean development environment. We recommend the [Ubuntu 16.04 docker image](https://hub.docker.com/_/ubuntu/) that can be found on Docker Hub 

## Development server for ClientApp
Step into the `ClientApp` directory (`cd ClientApp/`) and run `npm start` or `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## File Structure

Below is the basic structure that you should concern yourself with.

```
ClientApp --  src -- app --
                           |-- components -> Angular2 components that make up the application
                             |-- footer -> the app's footer
                             |-- header -> the app's header
                             |-- main-content -> the app's main content, 
                               |-- shared
                                 |-- search-input-card -> the card used to display the search box
                                 |-- search-result-table -> the table used to display the results
                                 |-- welcome-card -> a friendly greeting card
                           |-- mock -> the example data
                           |-- models
                           |-- services -> *this is where you wire up the API*
                           |-- app.component -> main app component
                           |-- config.ts -> Configution strings, such as API urls. *You may need to change this*

ServerApp -- -> this is where you much do the Primary Task
            | -- data.json -> the data for you to use
```


## What is required of you

#### Angular2 Front-end

The `ApiDataService` looks like this:
```
@Injectable()
export class ApiDataService {

    constructor(private http:Http) {
    }

    public performSearchRequest(searchTerm:string, queryType:string):Promise<SearchResult[]> {
        return new Promise<SearchResult[]>((resolve, reject) => {
            let url = Config.apiBaseUrl + Config.searchApi;
            url += "?s=" + searchTerm;

            console.log("Your query to be: " + url);

            if (queryType == 'mock') {
                //for now, fetching mock data! Not filtered by search query as that would be giving it away ;)
                resolve(MockSearchData);
            } else {
                //use reject(error) to return an error back
                reject("To be completed!");
            }
        });
    }
}
```

It needs to be expanded/modified to work your NodeJS/Express server. This is pretty much the only modification you should have to do to the `ClientApp`, as everything is wired up.

This can only be completed once you complete the primary task, but this is presented first so that you have a good idea of what is expected from the API.

# \*Primary Task\* NodeJS / ExpressJS Api server

This is the primary task. Complete the app in the `ServerApp` sub-directory.

###### Resources

* [NodeJS](https://nodejs.org/)
* [NPM](https://www.npmjs.com/)
* [ExpressJS](https://expressjs.com)

###### Requirements 

Your task is to build an API, using NodeJS and ExpressJS

1. To get an idea of what needs to happen, Hit the submit button without any value in the search box, and you will see it populate a table with results. It is up to you to replicate this.
2. Please complete the server application in the `ServerApp` sub-directory
3. Run `npm init` to get started. Build a simple NodeJS project, complete with `package.json`. We should be able to `npm install` to install the dependencies after we clone your source
4. Use ExpressJS to create a simple API server that accepts a query string. 
   Hints: a. You will need to "body-parser" JSON
          b. You will need CORS handling
5. Read the file `data.json` into the application and return a **filtered list based on the search term** to the `ClientApp`
6. Move over to the `ApiDataService` in the `ClientApp`, modify it to make the request to your API server
7. Process the response and resolve the `Promise` to present your data to the `ClientApp`
8. If you don't modify the structure of the data returned, then the `ClientApp` should display a table with your results

###### Git & Committing

Please be sure to "show your working out" by committing as much as possible. 
Even though you could create one commit for the entire solutions, this is discouraged. 
We would like to see the steps/process you used to arrive to your solution.

###### Bonus Requirements 

Look in `main-content.component.ts` and `main-content.component.html` to complete these

1. **BONUS:** Handle errors returned from the backed, "query string blank" and/or any other errors you might one to return, like 404 not found. For now, you will see an error being presented with a simple `alert()`, additional bonus points will be added for a creative expansion of the `ClientApp` to present an error in a more user-friendly way.
2. **BONUS:** Handle "no results found" when returned from the backend

## Why do this for us?

Completing this test will help us understand to what degree you satisfy the following criteria:

1. Aptitude, can you accomplish the task set forth using the Power of the Internet?
2. Precision, can you edit just what needs to be edited in order to accomplish your goals?
3. Attention, can you follow the guide set forth by the architect?

# Good luck & thanks!