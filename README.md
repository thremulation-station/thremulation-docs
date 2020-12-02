# thremulation.io ![build-site-status](https://github.com/mocyber/thremulation.io/workflows/build-site-preview/badge.svg)

This repository will host the user guide website via github pages.

Status tracker in: [issue #19](https://github.com/mocyber/thremulation-station/issues/19)


### Contribution

Instructions on how to spin up a local instance of mkdocs and following steps
to add to the project can be found in the [contribution guide](contribution-guide.md).  

This project is in constant developtment. If you want to jump in, open an issue!  


### Hasty Deployment

If you just want to see the current version of checked-in content, use the local-deploy script.

1. Ensure that you're in the `thremulation.io` repository.
1. Execute the local deployment script to serve the contents of the `docs/` folder on your local machine:

- Start python webserver: `sh local-deploy.sh`
- Browse to: `http://localhost:8000`
