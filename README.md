# Whackamole (Tech Play Academy 02)

The App Recipe is a concise breakdown of all the necessary steps to building out an application that includes a UI.

But in actuality, building an app is usually messier than a step-by-step process; It requires understanding of the problem at a high level and a solid roadmap, but not all the granular details are discovered yet. Then, as we begin building certain parts that we know we will need, we begin to uncover some of those details and the implementation details for everything becomes clearer as we go. And we implement various parts as we go to string it together. Point: It's not a perfect process.

In this sprint, you will be exploring this "messy" organic process by following a series of Checkpoints. The steps you will be exposed to here is an actual sequence of steps that an engineer used to solve this exact problem.

Each checkpoint will give you some guidance on _what you're trying to accomplish_ and any necessary outside resources, but you will be on your own in figuring out the exact implementation. (With our support during core time)

When you finish the checkpoint, you can `git commit` it so you don't lose your work, then `git checkout` the next checkpoint and the answer for the previous checkpoint will be supplied.

Read the [Git Workflow](#git-workflow) before you get started.

# Git Workflow

1. [ ] Begin by **forking** this repository.

![forking](https://i.imgur.com/PmLC0ON.png)

2. [ ] Then, clone down your fork: `git clone YOUR_FORK_URL`

3. [ ] Then, checkout the appropriate checkpoint branch. Example: for checkpoint 0:

`git checkout checkpoint-0` (checkpoint-0 is the branch name)

4. [ ] Read `checkpoints/checkpoint-0.md` (for checkpoint 0)

5. [ ] Do some work, then make a commit using `git commit`. 

6. [ ] Once you finish the work for a checkpoint, checkout the next branch. Example: `git checkout checkpoint-1`

7. [ ] Continue working until you finish!

# Starting the App

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev
```

Building the app for production:

```
# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
