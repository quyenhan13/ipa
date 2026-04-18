platform :ios, '15.5'

# Chỉ dùng CocoaPods public CDN
source 'https://cdn.cocoapods.org/'

require_relative './plugins.rb'

target 'vteeniovn' do
  use_frameworks!

  # Pods cần thiết (public)
  pod 'GoNativeCore'
  pod 'SSZipArchive', '~> 2.6.0'

  use_plugins!
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|

      # Tránh conflict version iOS
      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'

      # Fix build CI + TrollStore
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
      config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      config.build_settings['CODE_SIGNING_REQUIRED'] = 'NO'
      config.build_settings['CODE_SIGN_IDENTITY'] = ''
      config.build_settings['DEVELOPMENT_TEAM'] = ''
      config.build_settings['CODE_SIGN_STYLE'] = 'Manual'

    end
  end
end
