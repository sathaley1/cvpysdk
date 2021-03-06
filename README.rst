CVPySDK
=======

CVPySDK is a Python Package for Commvault Software.

CVPySDK uses Commvault REST API to perform operations on a Commcell via WebConsole.


Requirements
------------

- Python 2.7 or above
- **requests** Python package (https://pypi.python.org/pypi/requests/)
- **future** Python package (https://pypi.python.org/pypi/future)
- **xmltodict** Python package (https://pypi.python.org/pypi/xmltodict)
- Commvault Software v11 SP7 or later release with WebConsole installed


Installing CVPySDK
------------------

CVPySDK is available on GitHub (https://github.com/CommvaultEngg/cvpysdk).

It can be installed from source. After downloading, from within the ``cvpysdk`` directory, execute::

    python setup.py install


Using CVPySDK
-------------

Login to Commcell:
    >>> from cvpysdk.commcell import Commcell
    >>> commcell = Commcell(webconsole_hostname, commcell_username, commcell_password)

Print all clients:
    >>> print(commcell.clients)

Get a client:
	>>> client = commcell.clients.get(client_name)

Get an agent:
	>>> agent = client.agents.get(agent_name)

Get a backupset:
	>>> backupset = agent.backupsets.get(backupset_name)

Get a subclient:
	>>> subclient = backupset.subclients.get(subclient_name)

Run backup for a backupset:
	>>> job = backupset.backup()

Run backup for a subclient:
	>>> job = subclient.backup(backup_level, incremental_backup, incremental_level)

Browsing content of a subclient:
	>>> paths, dictionary = subclient.browse(path, show_deleted_files, vm_file_browse, vm_disk_browse)

Browsing content of a subclient in a specific time range:
	>>> paths, dictionary = subclient.browse_in_time(path, show_deleted_files, restore_index, from_date, to_date)

Searching a file in subclient backup content:
	>>> paths, dictionary = subclient.find(file_or_folder_name, show_deleted_files, restore_index)

Run restore in place job for a subclient:
	>>> job = subclient.restore_in_place(paths, overwrite, restore_data_and_acl)

Run restore out of place job for a subclient:
	>>> job = subclient.restore_out_of_place(client, destination_path, paths, overwrite, restore_data_and_acl)

Job Operations:
	>>> job.pause()		    # Suspends the Job
	>>> job.resume()	    # Resumes the Job
	>>> job.kill()		    # Kills the Job
	>>> job.status		    # Current Status the Job  --  Completed / Pending / Failed / .... / etc.
	>>> job.finished	    # Job finished or not     --  True / False
	>>> job.delay_reason	    # Job delay reason (if any)
	>>> job.pending_reason	    # Job pending reason (if any)


Uninstalling
------------

On Windows, if CVPySDK was installed using an ``.exe`` or ``.msi``
installer, simply use the uninstall feature of "**Add/Remove Programs**" in the
Control Panel.

Alternatively, you can uninstall using the **pip** command::

	pip uninstall cvpysdk

	
Contribution Guidelines
-----------------------

1. We welcome all the enhancements from everyone although we request the developer to follow some guidelines while interacting with the ``CVPySDK`` codebase.

2. Before adding any enhancements/bug-fixes, we request you to open an Issue first.

3. The SDK team will go over the Issue and notify if it is required or already been worked on.

4. If the Issue is approved, the contributor can then make the changes to their fork and open a pull request.

Pull Requests
*************
- CVPySDK has 3 branches, namely:
    - **master**
    - **dev**
    - **test**

- The contributor should *Fork* the **dev** branch, and make their changes on top of it, and open a *Pull Request*
- The **test** branch will Synced with the **dev** branch after every **n** commits, depending on the commit size
- The **master** branch will then be updated with the **test** branch, once everything is verified

 **Note:** The SDK team will not accept any *Pull Requests* on the **master** branch

Coding Considerations
*********************

- All python code should be **PEP8** compliant.
- All changes should be consistent with the design of the SDK.
- The code should be formatted using **autopep8** with line-length set to **99** instead of default **79**.
- All changes and any new methods/classes should be properly documented.
- The doc strings should be of the same format as existing docs.

Code of Conduct
***************

Everyone interacting in the **CVPySDK** project's codebases, issue trackers,
chat rooms, and mailing lists is expected to follow the
`PyPA Code of Conduct`_.

.. _PyPA Code of Conduct: https://www.pypa.io/en/latest/code-of-conduct/


License
=======
**CVPySDK** and its contents are licensed under Commvault License: https://raw.githubusercontent.com/CommvaultEngg/cvpysdk/master/LICENSE.txt


About Commvault
===============
.. image:: https://upload.wikimedia.org/wikipedia/en/thumb/1/12/Commvault_logo.png/150px-Commvault_logo.png
    :align: center

|

`Commvault <https://www.commvault.com/>`_
(NASDAQ: CVLT) is a publicly traded data protection and information management software company headquartered in Tinton Falls, New Jersey.

It was formed in 1988 as a development group in Bell Labs, and later became a business unit of AT&T Network Systems. It was incorporated in 1996.

Commvault software assists organizations with data backup and recovery, cloud and infrastructure management, and retention and compliance.
