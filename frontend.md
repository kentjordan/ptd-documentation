## Getting started

Before you can rightly use this frontend, the backend server must be started first.

## Running the project

**Prerequisites**

- Node.js v18.16.1

Before starting the project, we have to install the dependencies then change some **_important_** stuffs in a particular files

1.  Install dependencies by running:

    `npm install`

2.  Change the **SERVER_IP** and **SERVER_PORT** in /src/api/index.ts

        `const  SERVER_IP  =  '<your server's IP here>';`
        `const  SERVER_PORT  =  '<your server's PORT here>';`

        and, for the images that will be fetched from other host, add your server's IP/hostname in `remotePatterns` in /next.config.js
        ```
        const  nextConfig  =  {
        	reactStrictMode:  false,
        		images:  {
        			remotePatterns:  [{ hostname:  "<your server's IP/hostname here>"}],
        		}
        };
        ```

    Once you've all set, you can start now your frontend.

**Development**

    npm run dev

**Production**

1.  First, we build the project by running this command

        npm run build

2.  then, start the project by

        npm run start

If you are on your local machine, you can now open [http://localhost:3000](http://localhost:3000/) with your browser to see the result. If you host this on https it can't communicate to the backend, the backend only serves http requests.
