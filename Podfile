platform :ios, '15.5'

# Sources
source 'https://cdn.cocoapods.org/'
source 'https://github.com/gonativeio/gonative-specs.git'  # cần nếu dùng MedianIcons

require_relative './plugins.rb'

target 'vteeniovn' do
  use_frameworks!

  # Pods chính
  pod 'GoNativeCore'
  pod 'SSZipArchive', '~> 2.6.0'

  # ⚠️ MedianIcons (có thể gây lỗi nếu repo private)
  begin
    pod 'MedianIcons'
  rescue
    puts "⚠️ Bỏ qua MedianIcons (không có quyền repo)"
  end

  use_plugins!
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|

      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'

      # Fix CI + TrollStore
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
