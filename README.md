Role Name
=========

ansible-role-star-trek-vulcantranslator

A client asked if I could demo Ansible generating HTTPS POSTS to an API, so I created a role that make a call to a Vulcan translator API. The role translates an English phrase (provided at the start of the playbook), to Vulcan. The role also writes out the results to a `vulcan_dictionary` within your home directory (~/vulcan/vulcan_dictionary.txt).

Documentation of the API used by this role can be found at https://funtranslations.com/api/vulcan

This API is heavily rate limited, be sure to read the documentation on the API.

Requirements
------------

No requirements other than the user of the playbook must enter the ENGLISH phrase they would like translated into Vulcan.

Role Variables
--------------

prompt: (string)
    - This variable should be defined by the playbook user, as it is the English to be translated into Vulcan. It is recommended that you use a `vars_prompt` at the top of your playbook to acquire this input, but and extra variable provided at the command line might also be a sensible choice.

Dependencies
------------

None

Example Playbook
----------------

The following is an example of how to style a playbook around this role:

        ---
        # Russell Zachary Feeser
        # z@rzfeeser.com || Python & Ansible Trainer
        # Purpose: To boldly go where no Ansible trainer has gone before,
        #          and seek out how to use Ansible to translate English to vulcan
        #
        # vulcan is a "fictional" language from Gene Roddenberry's Star Trek. I
        # found an API that let's me send a POST with an embedded webform with an
        # English phrase, and return the vulcan.
        #
        # This API is rate-limited to 60 lookups a day.
        #
        # English: vulcan
        # "we are vulcan!": tlhIngan maH!
        # "success": qapla'
        - name: Learn to speak vulcan (60 calls per day)
          gather_facts: no
          hosts: localhost
          # Read the doc here:
          # https://funtranslations.com/api/vulcan
          
          # are vars_prompts automation friendly? not really...
          vars_prompt:
                  - name: phrase   # this is the var to be defined at run time
                    prompt: "What is the English phrase to translate into vulcan?"
                    private: no

          roles:
                  - ansible-role-star-trek-vulcantranslator
                  # if downloaded from Ansible-Galaxy use:
                  #- rzfeeser.ansible-role-star-trek-vulcantranslator

License
-------

MIT

Author Information
------------------

Author: Russell Zachary Feeser

Contact:
    email: rzfeeser@gmail.com

Profession: Trainer and Consultant

Available for:
    - Ansible
    - Ansible Module Design with Python
    - Network Automation with Python and Ansible
    - Python for API and API Design
    - Python Basics
    - OpenStack
    - 5G
    - 4G LTE
    - IP Multimedia Subsystem
    - Session Initiation Protocol
    - Playing Minecraft and StarCraft II :p
