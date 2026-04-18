platform :ios, '15.5'

source 'https://cdn.cocoapods.org/'

target 'vteeniovn' do
  use_frameworks!

  # ❌ Bỏ GoNativeCore
  # pod 'GoNativeCore'

  pod 'SSZipArchive', '~> 2.6.0'
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings.delete 'IPHONEOS_DEPLOYMENT_TARGET'

      config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      config.build_settings['CODE_SIGNING_REQUIRED'] = 'NO'
      config.build_settings['CODE_SIGN_IDENTITY'] = ''
    end
  end
end
