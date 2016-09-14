Site (v2.0.1)
====

Generate website configurations for use with Nginx (soon others like Apache)

Requirements
------------

- Nginx (Apache soon)
- Nginx and PHP optional

Role Variables
--------------

- **site_mode**: http
- **site_domain**: example.com
- **site_redirect**: false
- **site_root**: public
- **site_password**: false
- **site_password_file**: false
- **site_ssl_key**: false
- **site_ssl_crt**: false
- **site_websockets**: false
- **site_redirects**: []
- **site_proxy**: false
- **site_proxy_name**: myproxy
- **site_proxy_ip**: 127.0.0.1
- **site_proxy_port**: 3000

Dependencies
------------

- ryanlelek.nginx

Example Playbook
----------------

    - hosts: web
      become: yes
      roles:
        - ryanlelek.nginx

        # Redirect Snooping Visitors
        # Who found us by IP
        - role: ryanlelek.site
          site_domain: default
          redirect: https://www.google.com

        # HTTPS Site
        - role: ryanlelek.site
          site_domain: www.yourdomain.com
          site_mode: https
          site_ssl_key: ./path_to_rsa.key
          site_ssl_crt: ./path_to_rsa.crt
          site_root: test_files

      # See Also: ryanlelek.git_repo
      # That way you can pull files from a repository
      tasks:
        - name: Copy Site Files
          copy: src=./test_files dest=/home/{{ ansible_ssh_user }} owner={{ ansible_ssh_user }} group=sudo mode=0755

License
-------

MIT

Author Information
------------------

Created by [Ryan Lelek](https://www.ryanlelek.com)  
Part of [AnsibleTutorials.com](http://www.ansibletutorials.com)
