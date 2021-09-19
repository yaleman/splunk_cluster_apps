The contents of this repository goes in /opt/splunk/etc/deployment-apps/ on the splunk deployment server.

# Github actions

This will automatically run some basic config checks with [ksconf](https://ksconf.readthedocs.io/en/latest/).

To manually check the configuration before you commit, run the following:

```find . -type f -name '*.conf' | ksconf check -```

You should get a list of files checked, and a confirmation that there were 0 failures, similar to this. Please don't submit a change without checking this and fixing the errors!

    Completed checking 182 files.  rc=0 Breakdown:
    182 files were parsed successfully.
    0 files failed.

# Manually updating the data on the deployment server

1. Connect to the deployment server using SSH or SSM
2. Move into the directory `cd /opt/splunk/etc/deployment-apps/`
3. Run the pull as the splunk user (who should have the ssh config with the read-only key) `sudo -u splunk git pull`
4. Reload the app config within Splunk `sudo -u splunk /opt/splunk/bin/splunk reload deploy-server`
5. Check the deployment server interface to make sure the config's right.

Full command: `cd /opt/splunk/etc/deployment-apps/ && sudo -u splunk git pull && sudo -u splunk /opt/splunk/bin/splunk reload deploy-server`


