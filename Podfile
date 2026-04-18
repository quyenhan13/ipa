platform :ios, '15.5'

# Chỉ dùng CDN công khai, bỏ private spec của GoNative
source 'https://cdn.cocoapods.org/'

require_relative './plugins.rb'

target 'vteeniovn' do
  use_frameworks!

  # Pods cho Median / GoNative
  pod 'GoNativeCore'
  pod 'MedianIcons'
  pod 'SSZipArchive', '~> 2.6.0'

  use_plugins!

  target 'MedianIOSTests' do
    inherit! :search_paths
  end
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
      config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      config.build_settings['CODE_SIGNING_REQUIRED'] = 'NO'
      config.build_settings['CODE_SIGN_IDENTITY'] = ''
      config.build_settings['DEVELOPMENT_TEAM'] = ''
      config.build_settings['CODE_SIGN_STYLE'] = 'Manual'
      config.build_settings['EXPANDED_CODE_SIGN_IDENTITY'] = ''
    end
  end
end
