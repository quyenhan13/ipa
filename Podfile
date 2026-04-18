platform :ios, '15.5'

source 'https://cdn.cocoapods.org/'

target 'vteeniovn' do
  use_frameworks!

  # ✔️ Only stable public pod
  pod 'SSZipArchive', '~> 2.6.0'

  target 'MedianIOSTests' do
    inherit! :search_paths
  end
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '15.5'

      # disable signing for CI
      config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      config.build_settings['CODE_SIGNING_REQUIRED'] = 'NO'
      config.build_settings['CODE_SIGN_IDENTITY'] = ''
      config.build_settings['DEVELOPMENT_TEAM'] = ''
      config.build_settings['CODE_SIGN_STYLE'] = 'Manual'
    end
  end
end
