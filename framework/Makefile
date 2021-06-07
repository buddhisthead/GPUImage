PROJECT = GPUImage.xcodeproj
SCHEME = GPUImageFramework
XCFRAMEWORK = GPUImage.xcframework
BUILD_DIR = ./.framework_builds
DEVICE_SLICE = $(BUILD_DIR)/GPUImage-iphoneos.xcarchive
SIMULATOR_SLICE = $(BUILD_DIR)/GPUImage-iphonesimulator.xcarchive

all: $(XCFRAMEWORK)

clean:
	rm -fr $(DEVICE_SLICE) $(SIMULATOR_SLICE) $(XCFRAMEWORK)

DEVICE_SLICE:
	xcodebuild archive -project $(PROJECT) -scheme $(SCHEME) -archivePath $(DEVICE_SLICE) -sdk iphoneos SKIP_INSTALL=NO

SIMULATOR_SLICE:
	xcodebuild archive -project $(PROJECT) -scheme $(SCHEME) -archivePath $(SIMULATOR_SLICE) -sdk iphonesimulator SKIP_INSTALL=NO

$(XCFRAMEWORK): DEVICE_SLICE SIMULATOR_SLICE
	xcodebuild -create-xcframework -framework $(SIMULATOR_SLICE)/Products/Library/Frameworks/GPUImage.framework -framework $(DEVICE_SLICE)/Products/Library/Frameworks/GPUImage.framework -output $(XCFRAMEWORK)
