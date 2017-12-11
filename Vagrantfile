Vagrant.configure("2") do |config|
    #Creating first nginx box
    config.vm.define "webserver01" do |ws1|
    ws1.vm.box = "ubuntu/xenial64"
        ws1.vm.provider "virtualbox" do |vm1|
            vm1.name = "webserver01"
            vm1.memory = 1024
            vm1.cpus = 1
        end
    ws1.vm.hostname = "webserver01"
    ws1.vm.network "private_network", ip: "192.168.56.196"
    end

    #Creating second nginx box
    config.vm.define "webserver02" do |ws2|
        ws2.vm.box = "ubuntu/xenial64"
        ws2.vm.provider "virtualbox" do |vm2|
            vm2.name = "webserver02"
            vm2.memory = 1024
            vm2.cpus = 1
        end
    ws2.vm.hostname = "webserver02"
    ws2.vm.network "private_network", ip: "192.168.56.197"
    end

    #Creating haproxy
    config.vm.define "haproxy01" do |ha|
        ha.vm.box = "ubuntu/xenial64"
        ha.vm.provider "virtualbox" do |vm3|
            vm3.name = "haproxy01"
            vm3.memory = 1024
            vm3.cpus = 1
        end
    ha.vm.hostname = "haproxy01"
    ha.vm.network "private_network", ip: "192.168.56.198"
    end
end