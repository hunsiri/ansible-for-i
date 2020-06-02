..
.. SPDX-License-Identifier: Apache-2.0
..

:github_url: https://github.com/LiJunBJZhu/i_collection_core/tree/master/plugins/modules/ibmi_device_vary.py


ibmi_device_vary -- vary on or off target device on a remote IBMi node
======================================================================

.. contents::
   :local:
   :depth: 1


Synopsis
--------

vary on or off target device on a remote IBMi node.

For non-IBMi targets, no need






Parameters
----------

  status (True, str, None)
    ``on``/``off`` are idempotent actions that will not run commands unless necessary.

    ``reset`` will always bounce the service.

    **At least one of status are required.**


  extra_parameters (optional, str,  )
    extra parameter is appended at the end of VARYCFG command


  device_list (True, list, None)
    The name of the device


  joblog (optional, bool, False)
    If set to ``true``, append JOBLOG to stderr/stderr_lines.







See Also
--------

.. seealso::

   :ref:`service_module`
      The official documentation on the **service** module.


Examples
--------

.. code-block:: yaml+jinja

    
    - name: start host server service
      ibmi_device_vary:
        device_list: ['IASP1', 'IASP2']
        state: '*ON'
        joblog: True



Return Values
-------------

  stderr_lines (always, list, ['CPF2111:Library TESTLIB already exists.'])
    The command standard error split in lines


  end (always, str, 2019-12-02 11:07:54.064969)
    The command execution end time


  job_log (always, str, [{'TO_MODULE': 'QSQSRVR', 'TO_PROGRAM': 'QSQSRVR', 'MESSAGE_KEY': '00000379', 'MESSAGE_TEXT': 'Printer device PRT01 not found.', 'TO_INSTRUCTION': '9369', 'FROM_MODULE': '', 'FROM_PROGRAM': 'QWTCHGJB', 'FROM_USER': 'CHANGLE', 'MESSAGE_TIMESTAMP': '2020-05-20-21.41.40.845897', 'MESSAGE_SECOND_LEVEL_TEXT': 'Cause . . . . . :   This message is used by application programs as a general escape message.', 'FROM_PROCEDURE': '', 'FROM_INSTRUCTION': '318F', 'MESSAGE_LIBRARY': 'QSYS', 'FROM_LIBRARY': 'QSYS', 'SEVERITY': '20', 'MESSAGE_TYPE': 'DIAGNOSTIC', 'TO_LIBRARY': 'QSYS', 'MESSAGE_ID': 'CPD0912', 'MESSAGE_SUBTYPE': '', 'ORDINAL_POSITION': '5', 'MESSAGE_FILE': 'QCPFMSG', 'TO_PROCEDURE': 'QSQSRVR'}])
    the job_log


  stdout (always, str, +++ success VRYCFG CFGOBJ(IASP1) CFGTYPE(*DEV) STATUS(*ON))
    The command standard output


  cmd (always, str, VRYCFG CFGOBJ(IASP1) CFGTYPE(*DEV) STATUS(*ON) )
    The command executed by the task


  start (always, str, 2019-12-02 11:07:53.757435)
    The command execution start time


  delta (always, str, 0:00:00.307534)
    The command execution delta time


  stderr (always, str, CPF2111:Library TESTLIB already exists)
    The command standard error


  rc (always, int, 255)
    The command return code (0 means success, non-zero means failure)


  stdout_lines (always, list, ['+++ success VRYCFG CFGOBJ(IASP1) CFGTYPE(*DEV) STATUS(*ON)'])
    The command standard output split in lines





Status
------




- This module is not guaranteed to have a backwards compatible interface. *[preview]*


- This module is maintained by community.



Authors
~~~~~~~

- Jin Yi Fan(@jinyifan)
