Vagrant.configure("2") do |config|
    config.vm.define "ws1" do |ws1|
    ws1.vm.box = "ubuntu/xenial64"
        ws1.vm.provider "virtualbox" do |vm1|
            vm1.name = "webserver01"
            vm1.memory = 1024
            vm1.cpus = 1
        end
    ws1.vm.hostname = "webserver01"
    ws1.vm.network "private_network", ip: "192.168.56.196"
    ws1.vm.provision "shell", path: "script/install_nginx.sh"
    ws1.vm.provision "file", source: "config/nginx.conf", destination: "/etc/nginx/nginx.conf"
    ws1.vm.provision "file", source: "content/page.html", destination: "/var/www/html/page.html"
    ws1.vm.provision "shell", inline: "sudo systemctl reload nginx"
    end

    config.vm.define "ws2" do |ws2|
        ws2.vm.box = "ubuntu/xenial64"
    #Creating nginx webserver02
        ws2.vm.provider "virtualbox" do |vm2|
            vm2.name = "webserver02"
            vm2.memory = 1024
            vm2.cpus = 1
        end
    ws2.vm.hostname = "webserver02"
    ws2.vm.provision "shell", path: "script/install_nginx.sh"
    ws2.vm.provision "file", source: "config/nginx.conf", destination: "/etc/nginx/nginx.conf"
    ws2.vm.provision "shell", inline: "sudo systemctl reload nginx"
    end

    #Creating haproxy
    config.vm.define "ha" do |ha|
        ha.vm.box = "ubuntu/xenial64"
        ha.vm.provider "virtualbox" do |vm3|
            vm3.name = "haproxy01"
            vm3.memory = 1024
            vm3.cpus = 1
        end
    ha.vm.hostname = "haproxy01"
    ha.vm.network "private_network", ip: "192.168.56.198"
    ha.vm.provision "shell", path: "script/install_haproxy.sh"
    ha.vm.provision "file", source: "config/haproxy.conf", destination: "/etc/haproxy/haproxy.conf"
    ha.vm.provision "shell", inline: "sudo systemctl reload haproxy"
    end
end
