## slackexp2csv -- slack.com export to csv

For some reason slack.com does not take an import in the same format of it's export (as of 2014/06/08).  They do accept csv.  See

 * https://vulk.slack.com/services/export
 * https://vulk.slack.com/services/import

This script simply converts an export from slack.com to the csv format they use.

It expects the export data from the zipfile they create to be in a directory.

The output is dumped to standard out.

## Usage

```
slackexp2csv <exportdir/>
```

### Notes

Example directory structure:

  * slackexport/
    - users.json
    - channels.json
      * channel1/
        - 2014-06-01.json
        - 2014-06-02.json
      * channel2/
        - 2014-06-02.json
        - 2014-06-03.json


### License

See [LICENSE file](LICENSE)
