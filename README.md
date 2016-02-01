Site
====

Generate website configurations for use with Nginx (soon others like Apache)

Requirements
------------

- Nginx (Apache soon)
- Nginx and PHP optional

Role Variables
--------------

- **site_domain**: example.com
- **site_www**: false
- **site_root**: public
- **site_password**: false
- **site_password_file**: false
- **site_ssl**: false
- **site_ssl_key**: false
- **site_ssl_crt**: false
- **site_websockets**: false
- **site_redirects**: []
- **site_proxy_name**: nodejs
- **site_proxy**: false
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
        - role: ryanlelek.site
          site_domain: yourdomain.com
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
