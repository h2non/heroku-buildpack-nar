# heroku-buildpack-nar

[Heroku Buildpack](https://devcenter.heroku.com/articles/buildpacks) to easily deploy and run nar app containers.

## Usage

Set up the Buildpack in your app:
```bash
heroku config:add BUILDPACK_URL=https://github.com/h2non/heroku-buildpack-nar.git --app <app>
```

Then create a file called `.nar_release` in the project root directory pointing to the URL of the binary:
```
http://s3.amazonaws.com/bucket/app-0.1.0-linux-x64.nar
```

Binary will be located in the Heroky build directory.
You use a different file name passing the environment variable, for instance: `RELEASE_FILENAME=download_url`

In order to execute the binary you must create a `Procfile`, optionally passing custom flags:
```yaml
web: bash my-binary --env $ENV --debug
```

## See also

- [heroku-buildpack-vendorbinaries](https://github.com/peterkeen/heroku-buildpack-vendorbinaries)
- [s3simple](https://github.com/paulhammond/s3simple)
- [Heroku Slug API](https://blog.heroku.com/archives/2013/12/20/programmatically_release_code_to_heroku_using_the_platform_api)

## Licence

MIT license - Tomas Aparicio
