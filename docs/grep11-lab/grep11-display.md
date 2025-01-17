# Displaying your GREP11 environment

## List Crypto Domains on your Hyper Protect Virtual Servers LPAR

1. List your available domains with the Hyper Protect Virtual Server CLI:

    ``` bash
    hpvs crypto list
    ```

    ???+ example "Example output"

        ```
        hpvs crypto list
        +---------------+--------+
        | CRYPTO.DOMAIN | STATUS |
        +---------------+--------+
        | 08.0016       | in use |
        | 0a.0016       | in use |
        +---------------+--------+
        ```

    A value of *in use* in the **STATUS** column indicates that each crypto domain has a GREP11 server connected to it.

## Display the GREP11 servers

1. Display the virtual servers running on the Hyper Protect Virtual Servers LPAR:

    ``` bash
    hpvs vs list
    ```

    ???+ example "Example output"
    
        ``` hl_lines="4-5"
        +----------------------+---------+-------------+---------------------------------------+
        | NAMES                | STATE   | STATUS      | IMAGE                                 |
        +----------------------+---------+-------------+---------------------------------------+
        | grep11-08-0016-9876  | running | Up 16 hours | ibmzcontainers/hpcs-grep11-prod:1.2.1 |
        | grep11-0a-0016-19876 | running | Up 16 hours | ibmzcontainers/hpcs-grep11-prod:1.2.1 |
        | monitoring           | running | Up 4 weeks  | ibmzcontainers/monitoring:1.2.1       |
        | collectd             | running | Up 4 weeks  | ibmzcontainers/collectd-host:1.2.1    |
        | hpvs_grafana         | running | Up 3 weeks  | jinxiong/hpvs_grafana:latest          |
        | prom0630_19          | running | Up 3 weeks  | jinxiong/prom0630:latest              |
        +----------------------+---------+-------------+---------------------------------------+
        ```

    Observe that there are two servers listed whose name starts with `grep11`.  These are the two GREP11 servers that we have provided. One accessible from host port 9876 and one from host port 19876.

    !!! note
        The list you see may differ from what is shown in our example, but you should see the two GREP11 servers whose names are highlighted in our example.

2. Display details about one of the GREP11 servers with this command:

    ``` bash
    hpvs vs show --name grep11-08-0016-9876
    ```

    ???+ example "Example output"

        ```
        +-------------+------------------------------+
        | PROPERTIES  | VALUES                       |
        +-------------+------------------------------+
        | Name        | grep11-08-0016-9876          |
        | Status      | Up 16 hours                  |
        | CPU         | 2                            |
        | Memory      | 2048                         |
        | Networks    | Network:bridge               |
        |             | IPAddress:172.31.0.4         |
        |             | Gateway:172.31.0.1           |
        |             | Subnet:16                    |
        |             | MacAddress:02:42:ac:1f:00:04 |
        |             |                              |
        |             |                              |
        | Ports       | LocalPort:9876/tcp           |
        |             | GuestPort:9876               |
        |             |                              |
        | Quotagroups | appliance_data               |
        |             |                              |
        | State       | running                      |
        +-------------+------------------------------+

        ```

3. **(Optional)** Feel free to run the `hpvs vs show` command against the other GREP11 server.

Please proceed to the next section of the lab.
