
￼Instructions for how to run your program:
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


An overview of design decisions:
I decided to try and keep this as simple as possible, while still proving application structure to support future growth. Vue router is an awesome tool, and I didn't NEED it for this single page application, but I wanted to set up the project so it can easily be exapnded upon. As far as project structure goes, I used the Vue CLI to spin up the groundwork and edited from there to fit my needs.

What language you picked and why:
I picked Vue.js because that's the language I'm currently using at work. It definitely was not the easiest choice, because I'm still learning it, but I wanted to use this challenge as an opportunity to continue to discover more about the language. Also, since it's a newer language, there were some problems I was running into that I coudn't even find documentation on. It was fun to power through it though.

Your process for verifying the correctness of you program:
Since I wanted to only spend about 2-4 hours on this project, I didn't add any testing. That is not my strongest area and I thought it might take too much time away from actually working on the app. So I checked correctness by console.logging everything, and then breaking everything to make sure it was actually working how I expected it to work.

What didn't you get to, or what else might you do with more time?
I would have liked to make this a full-stack application. Put the data in a db and make ReSTful calls- so I could update and persist the data - maybe experient with VueX for state management. I think that would have been super fun, but I wanted to stick to the instructions and not go toooooo crazy ;) I might come back and visit this later to turn it into a full-stack app!

Oh! Looking back now, I probably would have made each of those choice cards into 1 reusable component and import it into the index. Right now, the index.vue file is pretty long and repetitive.

Thanks so much for taking the time to look at my code challenge! Any feedback or advice would be must appreciated.