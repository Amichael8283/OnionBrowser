use_frameworks!

platform :ios, '15.0'

#source 'https://cdn.cocoapods.org/'
#source 'https://cocoapods-cdn.netlify.app/'
source 'https://github.com/CocoaPods/Specs.git'

target 'OnionBrowser' do
  pod 'DTFoundation/DTASN1'
  pod 'TUSafariActivity'

  pod 'SDCAlertView', '~> 10'
  pod 'FavIcon', :git => 'https://github.com/tladesignz/FavIcon.git'
  pod 'MBProgressHUD', '~> 1.2'
  pod 'Eureka', '~> 5.3'
  pod 'ImageRow', '~> 4.1'

  pod 'Tor/GeoIP',
  # '~> 408.4'
  :path => '../Tor.framework'

  pod 'IPtProxyUI',
  '~> 4.0'
  # :git => 'https://github.com/tladesignz/IPtProxyUI-ios'
  # :path => '../IPtProxyUI-ios'


  pod 'OrbotKit', '~> 1.1'
end

target 'OnionBrowser Tests' do
  pod 'OCMock'
  pod 'DTFoundation/DTASN1'
end

# Fix Xcode 14 code signing issues with bundles.
# See https://github.com/CocoaPods/CocoaPods/issues/8891#issuecomment-1249151085
post_install do |installer|
  installer.pods_project.targets.each do |target|
    if target.respond_to?(:product_type) and target.product_type == "com.apple.product-type.bundle"
      target.build_configurations.each do |config|
        config.build_settings['CODE_SIGNING_ALLOWED'] = 'NO'
      end
    end
    if target.respond_to?(:name) and !target.name.start_with?("Pods-")
      target.build_configurations.each do |config|
        config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '12.0'
      end
    end
  end
end
