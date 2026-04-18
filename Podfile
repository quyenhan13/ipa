# Uncomment the next line to define a global platform for your project
platform :ios, '15.5'

# Main CocoaPods spec repo (sử dụng CDN để nhanh hơn)
source 'https://cdn.cocoapods.org/'

# Tạm comment private spec của GoNative để build trên GitHub Actions
# source 'git@github.com:gonativeio/gonative-specs.git'

require_relative './plugins.rb'

target 'vteeniovn' do   # ← Đổi thành tên target đúng nếu khác
  use_frameworks!

  # Pods for GonativeIO
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
      # Xóa deployment target cũ để tránh conflict
      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'

      # Quan trọng cho TrollStore & CI
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
