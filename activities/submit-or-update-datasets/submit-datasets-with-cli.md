# Submit Datasets with CLI

## CLI

> If you can improve this process, click the link in the upper right to Edit on GitHub and make a PR!

1. [Install Dolt](https://docs.dolthub.com/getting-started/installation).
2. Fork the project to your DoltHub account (you will need to [create an account](https://www.dolthub.com/signin) if you don't have one).
3.  Clone down your copy of the repository.

    ```
    dolt clone <your account name>/datasets && cd datasets
    dolt table export datasets > datasets.csv
    ```
4.  Open the `datasets.csv` file, make changes, and save. Leave `id` blank—UUIDs are generated automatically. Make sure you're not adding a URL that already exists.

    ```
    dolt branch <branch name e.g. add-CA-counties>
    dolt checkout <your branch>
    dolt table import -u datasets datasets.csv
    ```
5.  Run this command to add your csv to your checked out branch.

    ```
    dolt add .
    ```
6.  Push the commit.

    ```
    dolt commit -m “<message e.g. added 5 Alameda County datasets>”
    dolt push --set-upstream origin <your branch>
    ```
7. Head to [https://www.dolthub.com/repositories/pdap/datasets/](https://www.dolthub.com/repositories/pdap/datasets/).
8. Create a [new Pull Request](https://www.dolthub.com/repositories/pdap/datasets/pulls/new) to merge your dataset into `master`. Select your fork as the from repository, and then your branch will appear as an option. Read more about DoltHub Pull Requests [here](https://docs.dolthub.com/dolthub/getting-started#pull-requests).
