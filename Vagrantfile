Vagrant.require_version ">= 1.8.0"

Vagrant.configure(2) do |config|
  ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

  config.vm.network "forwarded_port", id: 'ssh', guest: 22, host: 2202, auto_correct: false
  config.vm.network "forwarded_port", id: 'xrdp', guest: 3389, host: 33890, auto_correct: false

  config.ssh.insert_key = false
  config.ssh.username = "debian"
  config.ssh.password = "ChangeMe"

  config.vm.provider "docker" do |d|
    d.image = "frxyt/xrdp:cinnamon"
    #d.build_dir = "."
    d.has_ssh = true
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
  end
end
