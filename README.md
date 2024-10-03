# Mono Heroku Buildpack

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack) for Mono that will run [ASP.NET](http://friism.com/running-net-on-heroku) and [Katana/OWIN applications](http://friism.com/running-owin-katana-apps-on-heroku).

It uses [nginx](http://www.mono-project.com/FastCGI_Nginx) as the web server and runs on Mono 3.10.0.

## Usage

Additional details and guides:

 * [Running ASP.NET and .NET console apps on Heroku](http://friism.com/running-net-on-heroku)
 * [Running Katana/OWIN apps on Heroku](http://friism.com/running-owin-katana-apps-on-heroku)
 * [Buildpack update to Mono 3.2 and more](http://friism.com/heroku-net-buildpack-update-to-mono-3-2-and-more)
 * [Heroku .NET buildpack now with nginx](http://friism.com/heroku-net-buildpack-now-with-nginx)

Example usage:

    $ heroku create --buildpack http://github.com/friism/heroku-buildpack-mono.git
    $ git push heroku master

The buildpack will detect your app as ASP.NET if it has the file `global.asax` in the root or at one directory depth or as .NET if it has a `.sln` file.

## TODO
* Consider inserting environment variables and connectionstrings into Web.config
* Web.Release.config
* Figure out whether there's hope for EntityFramework (and reliance on `System.Data.Entity` and other)
* More Mono/XSP versions and ability to select version, like [Python buildpack](https://devcenter.heroku.com/articles/python-runtimes)
* Visual Basic!
* ~~Store buildoutput in $CACHE_DIR and do incremental builds (also won't cause NuGet packages to be re-downloaded)~~
* ~~Less simplistic nginx setup, see [nginx buildpack](https://github.com/ryandotsmith/nginx-buildpack)~~
* ~~Factor repeated code into functions like [PHP buildpack](https://github.com/CHH/heroku-buildpack-php/blob/master/bin/compile)~~
* ~~Remove original source code before slug is tarred up~~
* ~~Slim down Mono runtime to reduce slug size and build time~~
* ~~Avoid copying Mono runtime to build /app and ${BUILD_DIR} during build~~
* ~~Get bundling and minification to work (likely to be Win/Linux path issues)~~
* ~~Get default Visual Studio templates working (you just have to fix casing problems~~

## Compiling Binaries

 * [Building Heroku buildpack binaries with Docker](http://friism.com/building-heroku-buildpack-binaries-with-docker)
 
