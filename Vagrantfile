Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    #Creating nginx webserver01
        config.vm.provider "virtualbox" do |vm1|
        vm1.name = "webserver01"
        vm1.memory = 1024
        vm1.cpus = 1
    end
    config.vm.provision "shell", path: "script/install_nginx.sh"
    config.vm.provision "file", source: "config/nginx.conf", destination: "/etc/nginx/nginx.conf"
    config.vm.provision "shell", inline: "sudo systemctl reload nginx"

    #Creating nginx webserver02
        config.vm.provider "virtualbox" do |vm2|
        vm2.name = "webserver02"
        vm2.memory = 1024
        vm2.cpus = 1
    end
    config.vm.provision "shell", path: "script/install_nginx.sh"
    config.vm.provision "file", source: "config/nginx.conf", destination: "/etc/nginx/nginx.conf"
    config.vm.provision "shell", inline: "sudo systemctl reload nginx"

    #Creating haproxy
    config.vm.provider "virtualbox" do |vm3|
        vm3.name = "haproxy01"
        vm3.memory = 1024
        vm3.cpus = 1
    end
    config.vm.provision "shell", path: "script/install_haproxy.sh"
    config.vm.provision "file", source: "config/haproxy.conf", destination: "/etc/haproxy/haproxy.conf"
    config.vm.provision "shell", inline: "sudo systemctl reload haproxy"
end
