#
# This Vagrantfile will work with Windows, Mac, or Linux...
# HOWEVER, it will only support Linux and Mac for the CI tests
# If it was an absolute need, they could also be modified to run on Windows
#
# Hmmm, also, this can/should change to VBox to run in a cloud environment

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'Juniper/ffp-X46-D10.2'
  config.vm.network 'forwarded_port', guest: 830, host: 830
  config.vm.network 'forwarded_port', guest: 23, host: 23
  if RUBY_PLATFORM == '^x86_64-darwin.+' || RUBY_PLATFORM == '^linux.+'
    config.vm.provider 'vmware_fusion' do |v|
      v.vmx['serial0.present']  = 'TRUE'
      v.vmx['serial0.fileType'] = 'device'
      v.vmx['serial0.fileName'] = '\dev\ttyNETCONFGemTest'
    end
  end
  if RUBY_PLATFORM == '^win/i'
    config.vm.provider 'vmware_fusion' do |v|
      v.vmx['serial0.present']  = 'TRUE'
      v.vmx['serial0.fileType'] = 'pipe'
      v.vmx['serial0.pipe.endPoint'] = '\\\\.\pipe\com_1'
    end
  end
end
