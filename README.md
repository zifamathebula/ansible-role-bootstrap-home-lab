# ansible-role-setup-home-lab
An Ansible role for bootstrapping and securing an Ubuntu server, making it ready for deploying applications using Docker Compose and Kubernetes (k8s) in a home lab environment.

## Features

- Bootstraps a fresh Ubuntu server.
- Installs the latest updates and upgrades.
- Applies necessary configurations for securing the server, such as:
  - Disabling password authentication.
  - Allowing SSH access only with a key.
  - Closing off all ports except those explicitly required.
- Installs tooling for running deployable apps using Docker Compose and Kubernetes (k8s).

## Usage

### As a Role in Your Playbook

To use this Ansible role in your project, include it in your project's `requirements.yml` file, and then include the role in your playbook:

```yaml
- hosts: all
  roles:
    - secure-ubuntu-bootstrap
```
### Running Independently

To run this Ansible role independently, you can use the following steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/secure-ubuntu-bootstrap.git
   ```
   
2. Change to the repository directory:

   ```bash
   cd secure-ubuntu-bootstrap   
   ```
   
3. Create an inventory file named `inventory.ini` with your target server details, for example:
```ini
[myserver]
192.168.1.100 
ansible_user=ubuntu 
ansible_ssh_private_key_file=~/.ssh/id_rsa
```

4. Run the Ansible playbook using the provided example-playbook.yml:
```bash
ansible-playbook -i inventory.ini example-playbook.yml
```
      
## Acknowledgements

A special thanks to Jeff Geerling ([geerlingguy](https://github.com/geerlingguy)) for his invaluable contributions to the Ansible community. His expertise and dedication have been instrumental in shaping best practices and providing guidance to countless developers.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

We greatly appreciate any contributions to this project. Your help and expertise can make this Ansible role even better. Here's how you can contribute:

1. **Report issues**: If you find any issues or have suggestions for improvements, please [open an issue](https://github.com/yourusername/secure-ubuntu-bootstrap/issues) on the GitHub repository. Be sure to include a detailed description and any relevant information to help reproduce or understand the issue.

2. **Submit pull requests**: If you have implemented a new feature or fixed a bug, feel free to submit a pull request. Before submitting, please make sure your changes follow the project's coding style and guidelines. Include a description of your changes, any relevant issue numbers, and a summary of testing performed.

3. **Improve documentation**: Help improve the documentation by fixing typos, clarifying instructions, or adding more examples. Submit your changes as a pull request for review.

4. **Share your experiences**: If you use this Ansible role in your project, share your experiences, challenges, and solutions with the community. Your feedback can provide valuable insights and help others succeed with their projects.

Thank you for considering a contribution to the `ansible-role-setup-home-lab` project!
