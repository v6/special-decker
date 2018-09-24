Vagrant.configure("2") do |config|
  ##  Set up one or more Run Deck Containers using Vagrant.
  ##  Host-only network does not seem to work.

  (1..1).each do |containernumber|
    config.vm.define "container#{containernumber}" do |container|
      container.vm.hostname = "rundeck#{containernumber}"
      container.vm.network "forwarded_port", guest: 4440, host: "4440#{containernumber}"
      container.vm.network :private_network, ip: "192.168.44.4#{containernumber}"
      container.vm.provider "docker" do |d|
        d.username = ENV['DOCKER_USER_NAME']
        print d.username
        d.password = ENV['DOCKER_PASS_PHRASE']
        d.image = "rundeck/rundeck:3.0.6"
      end
    end
  end
end
