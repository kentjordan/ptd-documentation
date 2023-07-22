## Getting started

Before you **can rightly use** the backend, the **database server must be started first**, in this case it's PostgreSQL v15.

## Setting up the project

**Prerequisites**

- Node.js v18.16.1

Before running the project, we have to install the dependencies first then change some **_important_** stuffs in a particular files. Follow these steps:

1.  Install the dependencies by running:

    `npm install`

    **NOTE:** Make sure you are in the project root dir/folder.

2.  Create the `.env` file in the project root dir/folder with these variables:

    ```
    SERVER_IP=<your server's IP/hostname here>
    SERVER_PORT=7777
    SECRET_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21wYW55IjoiR0VNIENPREUgSVQgU09MVVRJT05TIiwiZGV2IjoiS2VudCBKb3JkYW4iLCJpYXQiOjE1MTYyMzkwMjJ9.k90R5yGepS69v_QufpNb6682xwMYUErMGE6s1pZvHXs

    DATABASE_URL="postgresql://postgres:<password>@<db_ip>:5432/PeachTreeDesigns?schema=public"
    ```

3.  Change the **SERVER_IP** and **DATABASE_URL** credentials in `.env` file

- **SERVER_IP**:

  `SERVER_IP=<your server's IP/hostname here>`

  Replace `<your server's IP/hostname here>` into your server's IP

- **DATABASE_URL**:

  `DATABASE_URL=postgresql://postgres:<password>@<db_ip>:5432/PeachTreeDesigns?schema=public`

  Replace `<password>` with your password that you've set in your PostgreSQL and `<db_ip>` into your PostgreSQL's IP.

  e.g., `DATABASE_URL=postgresql://postgres:mypassword123@127.0.0.1:5432/PeachTreeDesigns?schema=public`

**NOTE: Before running the Prisma's commands make sure that you have already setup your PostgreSQL database. If not, prisma will not work especially the** `npx prisma db pull` command.

**Setup Prisma by running these commands**

1.  `npx prisma init`
2.  `npx prisma db pull`
3.  `npx prisma generate`

**Create these two folder (.uploaded_files and images) in project's root dir:**

`.uploaded_files/images`

Inside of the `.uploaded_files`, there must the `images` folder. **This must be done, if not the server can't accept the uploaded images from the admin frontend.**

Once you've all set, you can build and run your backend.

## Building and running the project

We first build the project before running it.

**Build the project**
`npm run build:prod`

**Run the project on production**

    `npm install -g pm2`
    `npm run start:prod`

You can now access the server through http://[IP/hostname]:7777

Done! You may proceed to setting up your admin frontend. 🚀🥳🎉
