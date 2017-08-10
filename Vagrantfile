Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.define "tinydns-unbound" do |machine|
    machine.vm.hostname = "tinydns-unbound.local"
    machine.vm.network "private_network", ip: "192.168.42.18"

    config.vm.provision :ansible,
      playbook: 'playbook.yml',
      groups: { local_dns: %w(tinydns-unbound) },
      raw_arguments: %w(-vv --diff),
      extra_vars: { hosts_group: "local_dns" },
      limit: :all
  end
end
