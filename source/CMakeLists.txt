function(irr_add_c_objects name)
	add_library(${name} OBJECT ${ARGN})
	set_target_properties(${name} PROPERTIES POSITION_INDEPENDENT_CODE ON)
endfunction()
irr_add_c_objects(irr_zlib
	zlib/adler32.c
	zlib/compress.c
	zlib/crc32.c
	zlib/deflate.c
	zlib/inffast.c
	zlib/inflate.c
	zlib/inftrees.c
	zlib/trees.c
	zlib/uncompr.c
	zlib/zutil.c
)
target_include_directories(irr_zlib PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/zlib)
irr_add_c_objects(irr_jpeg
	jpeglib/jcapimin.c
	jpeglib/jcapistd.c
	jpeglib/jccoefct.c
	jpeglib/jccolor.c
	jpeglib/jcdctmgr.c
	jpeglib/jchuff.c
	jpeglib/jcinit.c
	jpeglib/jcmainct.c
	jpeglib/jcmarker.c
	jpeglib/jcmaster.c
	jpeglib/jcomapi.c
	jpeglib/jcparam.c
	jpeglib/jcprepct.c
	jpeglib/jcsample.c
	jpeglib/jctrans.c
	jpeglib/jdapimin.c
	jpeglib/jdapistd.c
	jpeglib/jdatadst.c
	jpeglib/jdatasrc.c
	jpeglib/jdcoefct.c
	jpeglib/jdcolor.c
	jpeglib/jddctmgr.c
	jpeglib/jdhuff.c
	jpeglib/jdinput.c
	jpeglib/jdmainct.c
	jpeglib/jdmarker.c
	jpeglib/jdmaster.c
	jpeglib/jdmerge.c
	jpeglib/jdpostct.c
	jpeglib/jdsample.c
	jpeglib/jdtrans.c
	jpeglib/jerror.c
	jpeglib/jfdctflt.c
	jpeglib/jfdctfst.c
	jpeglib/jfdctint.c
	jpeglib/jidctflt.c
	jpeglib/jidctfst.c
	jpeglib/jidctint.c
	jpeglib/jmemmgr.c
	jpeglib/jmemnobs.c
	jpeglib/jquant1.c
	jpeglib/jquant2.c
	jpeglib/jutils.c
	jpeglib/jcarith.c
	jpeglib/jdarith.c
	jpeglib/jaricom.c
)
target_include_directories(irr_jpeg PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/jpeglib)
irr_add_c_objects(irr_png
	libpng/png.c
	libpng/pngerror.c
	libpng/pngget.c
	libpng/pngmem.c
	libpng/pngpread.c
	libpng/pngread.c
	libpng/pngrio.c
	libpng/pngrtran.c
	libpng/pngrutil.c
	libpng/pngset.c
	libpng/pngtrans.c
	libpng/pngwio.c
	libpng/pngwrite.c
	libpng/pngwtran.c
	libpng/pngwutil.c
)
target_include_directories(irr_png PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/libpng
	${CMAKE_CURRENT_SOURCE_DIR}/zlib)
target_compile_definitions(irr_png PRIVATE
	PNG_THREAD_UNSAFE_OK PNG_NO_MMX_CODE PNG_NO_MNG_FEATURES)
irr_add_c_objects(irr_bzip2
	bzip2/blocksort.c
	bzip2/huffman.c
	bzip2/crctable.c
	bzip2/randtable.c
	bzip2/bzcompress.c
	bzip2/decompress.c
	bzip2/bzlib.c
)
target_include_directories(irr_bzip2 PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/bzip2)
irr_add_c_objects(irr_lzma
	lzma/LzmaDec.c
)
target_include_directories(irr_lzma PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/lzma)
set(IRR_MESH_LOADER_SRCS
	CBSPMeshFileLoader.cpp
	CMD2MeshFileLoader.cpp
	CMD3MeshFileLoader.cpp
	CMS3DMeshFileLoader.cpp
	CB3DMeshFileLoader.cpp
	C3DSMeshFileLoader.cpp
	COgreMeshFileLoader.cpp
	COBJMeshFileLoader.cpp
	CColladaFileLoader.cpp
	CCSMLoader.cpp
	CDMFLoader.cpp
	CLMTSMeshFileLoader.cpp
	CMY3DMeshFileLoader.cpp
	COCTLoader.cpp
	CXMeshFileLoader.cpp
	CIrrMeshFileLoader.cpp
	CSTLMeshFileLoader.cpp
	CLWOMeshFileLoader.cpp
	CPLYMeshFileLoader.cpp
	CSMFMeshFileLoader.cpp
	CMeshTextureLoader.cpp
)
set(IRR_MESH_WRITER_SRCS
	CColladaMeshWriter.cpp
	CIrrMeshWriter.cpp
	CSTLMeshWriter.cpp
	COBJMeshWriter.cpp
	CPLYMeshWriter.cpp
	CB3DMeshWriter.cpp
)
set(IRR_MESH_SRCS
	CSkinnedMesh.cpp
	CBoneSceneNode.cpp
	CMeshSceneNode.cpp
	CAnimatedMeshSceneNode.cpp
	CAnimatedMeshMD2.cpp
	CAnimatedMeshMD3.cpp
	CQ3LevelMesh.cpp
	CQuake3ShaderSceneNode.cpp
	CAnimatedMeshHalfLife.cpp
)
set(IRR_SCENE_SRCS
	CBillboardSceneNode.cpp
	CCameraSceneNode.cpp
	CDummyTransformationSceneNode.cpp
	CEmptySceneNode.cpp
	CGeometryCreator.cpp
	CLightSceneNode.cpp
	CMeshManipulator.cpp
	CMetaTriangleSelector.cpp
	COctreeSceneNode.cpp
	COctreeTriangleSelector.cpp
	CSceneCollisionManager.cpp
	CSceneManager.cpp
	CShadowVolumeSceneNode.cpp
	CSkyBoxSceneNode.cpp
	CSkyDomeSceneNode.cpp
	CTerrainSceneNode.cpp
	CTerrainTriangleSelector.cpp
	CVolumeLightSceneNode.cpp
	CCubeSceneNode.cpp
	CSphereSceneNode.cpp
	CTextSceneNode.cpp
	CTriangleBBSelector.cpp
	CTriangleSelector.cpp
	CWaterSurfaceSceneNode.cpp
	CMeshCache.cpp
	CDefaultSceneNodeAnimatorFactory.cpp
	CDefaultSceneNodeFactory.cpp
	CSceneLoaderIrr.cpp
)
set(IRR_PARTICLE_SRCS
	CParticleAnimatedMeshSceneNodeEmitter.cpp
	CParticleBoxEmitter.cpp
	CParticleCylinderEmitter.cpp
	CParticleMeshEmitter.cpp
	CParticlePointEmitter.cpp
	CParticleRingEmitter.cpp
	CParticleSphereEmitter.cpp
	CParticleAttractionAffector.cpp
	CParticleFadeOutAffector.cpp
	CParticleGravityAffector.cpp
	CParticleRotationAffector.cpp
	CParticleSystemSceneNode.cpp
	CParticleScaleAffector.cpp
)
set(IRR_ANIMATOR_SRCS
	CSceneNodeAnimatorCameraFPS.cpp
	CSceneNodeAnimatorCameraMaya.cpp
	CSceneNodeAnimatorCollisionResponse.cpp
	CSceneNodeAnimatorDelete.cpp
	CSceneNodeAnimatorFlyCircle.cpp
	CSceneNodeAnimatorFlyStraight.cpp
	CSceneNodeAnimatorFollowSpline.cpp
	CSceneNodeAnimatorRotation.cpp
	CSceneNodeAnimatorTexture.cpp
)
set(IRR_DRIVER_SRCS
	CNullDriver.cpp
	COpenGLCacheHandler.cpp
	COpenGLDriver.cpp
	COpenGLNormalMapRenderer.cpp
	COpenGLParallaxMapRenderer.cpp
	COpenGLShaderMaterialRenderer.cpp
	COpenGLSLMaterialRenderer.cpp
	COpenGLExtensionHandler.cpp
	CD3D9Driver.cpp
	CD3D9HLSLMaterialRenderer.cpp
	CD3D9NormalMapRenderer.cpp
	CD3D9ParallaxMapRenderer.cpp
	CD3D9ShaderMaterialRenderer.cpp
	CD3D9Texture.cpp
	CGLXManager.cpp
	CWGLManager.cpp
)
set(IRR_IMAGE_SRCS
	CColorConverter.cpp
	CImage.cpp
	CImageLoaderBMP.cpp
	CImageLoaderDDS.cpp
	CImageLoaderJPG.cpp
	CImageLoaderPCX.cpp
	CImageLoaderPNG.cpp
	CImageLoaderPSD.cpp
	CImageLoaderPVR.cpp
	CImageLoaderTGA.cpp
	CImageLoaderPPM.cpp
	CImageLoaderWAL.cpp
	CImageLoaderRGB.cpp
	CImageWriterBMP.cpp
	CImageWriterJPG.cpp
	CImageWriterPCX.cpp
	CImageWriterPNG.cpp
	CImageWriterPPM.cpp
	CImageWriterPSD.cpp
	CImageWriterTGA.cpp
)
set(IRR_VIDEO_SRCS
	CVideoModeList.cpp
	CFPSCounter.cpp
)
set(IRR_SOFTWARE_RENDERER_SRCS
	CSoftwareDriver.cpp
	CSoftwareTexture.cpp
	CTRFlat.cpp
	CTRFlatWire.cpp
	CTRGouraud.cpp
	CTRGouraudWire.cpp
	CTRNormalMap.cpp
	CTRStencilShadow.cpp
	CTRTextureFlat.cpp
	CTRTextureFlatWire.cpp
	CTRTextureGouraud.cpp
	CTRTextureGouraudAdd.cpp
	CTRTextureGouraudNoZ.cpp
	CTRTextureGouraudWire.cpp
	CZBuffer.cpp
	CTRTextureGouraudVertexAlpha2.cpp
	CTRTextureGouraudNoZ2.cpp
	CTRTextureLightMap2_M2.cpp
	CTRTextureLightMap2_M4.cpp
	CTRTextureLightMap2_M1.cpp
	CSoftwareDriver2.cpp
	CSoftwareTexture2.cpp
	CTRTextureGouraud2.cpp
	CTRGouraud2.cpp
	CTRGouraudAlpha2.cpp
	CTRGouraudAlphaNoZ2.cpp
	CTRTextureDetailMap2.cpp
	CTRTextureGouraudAdd2.cpp
	CTRTextureGouraudAddNoZ2.cpp
	CTRTextureWire2.cpp
	CTRTextureLightMap2_Add.cpp
	CTRTextureLightMapGouraud2_M4.cpp
	IBurningShader.cpp
	CTRTextureBlend.cpp
	CTRTextureGouraudAlpha.cpp
	CTRTextureGouraudAlphaNoZ.cpp
	CDepthBuffer.cpp
	CBurningShader_Raster_Reference.cpp
)
set(IRR_IO_SRCS
	CFileList.cpp
	CFileSystem.cpp
	CLimitReadFile.cpp
	CMemoryFile.cpp
	CReadFile.cpp
	CWriteFile.cpp
	CXMLReader.cpp
	CXMLWriter.cpp
	CWADReader.cpp
	CZipReader.cpp
	CPakReader.cpp
	CNPKReader.cpp
	CTarReader.cpp
	CMountPointReader.cpp
	irrXML.cpp
	CAttributes.cpp
)
set(IRR_OTHER_SRCS
	CIrrDeviceSDL.cpp
	CIrrDeviceLinux.cpp
	CIrrDeviceConsole.cpp
	CIrrDeviceStub.cpp
	CIrrDeviceWin32.cpp
	CIrrDeviceFB.cpp
	CLogger.cpp
	COSOperator.cpp
	Irrlicht.cpp
	os.cpp
	leakHunter.cpp
	CProfiler.cpp
	utf8.cpp
)
set(IRR_GUI_SRCS
	CGUIButton.cpp
	CGUICheckBox.cpp
	CGUIComboBox.cpp
	CGUIContextMenu.cpp
	CGUIEditBox.cpp
	CGUIEnvironment.cpp
	CGUIFileOpenDialog.cpp
	CGUIFont.cpp
	CGUIImage.cpp
	CGUIInOutFader.cpp
	CGUIListBox.cpp
	CGUIMenu.cpp
	CGUIMeshViewer.cpp
	CGUIMessageBox.cpp
	CGUIModalScreen.cpp
	CGUIScrollBar.cpp
	CGUISpinBox.cpp
	CGUISkin.cpp
	CGUIStaticText.cpp
	CGUITabControl.cpp
	CGUITable.cpp
	CGUIToolBar.cpp
	CGUIWindow.cpp
	CGUIColorSelectDialog.cpp
	CDefaultGUIElementFactory.cpp
	CGUISpriteBank.cpp
	CGUIImageList.cpp
	CGUITreeView.cpp
	CGUIProfiler.cpp
)
set(IRR_AES_SRCS
	aesGladman/aescrypt.cpp
	aesGladman/aeskey.cpp
	aesGladman/aestab.cpp
	aesGladman/fileenc.cpp
	aesGladman/hmac.cpp
	aesGladman/prng.cpp
	aesGladman/pwd2key.cpp
	aesGladman/sha1.cpp
	aesGladman/sha2.cpp
)
add_library(Irrlicht
	${IRR_MESH_LOADER_SRCS}
	${IRR_MESH_WRITER_SRCS}
	${IRR_MESH_SRCS}
	${IRR_SCENE_SRCS}
	${IRR_PARTICLE_SRCS}
	${IRR_ANIMATOR_SRCS}
	${IRR_DRIVER_SRCS}
	${IRR_IMAGE_SRCS}
	${IRR_VIDEO_SRCS}
	${IRR_SOFTWARE_RENDERER_SRCS}
	${IRR_IO_SRCS}
	${IRR_OTHER_SRCS}
	${IRR_GUI_SRCS}
	${IRR_AES_SRCS}
	$<TARGET_OBJECTS:irr_zlib>
	$<TARGET_OBJECTS:irr_jpeg>
	$<TARGET_OBJECTS:irr_png>
	$<TARGET_OBJECTS:irr_bzip2>
	$<TARGET_OBJECTS:irr_lzma>
)
target_include_directories(Irrlicht
	PUBLIC
		$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
		$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/irrlicht>
	PRIVATE
		${CMAKE_CURRENT_SOURCE_DIR}/zlib
		${CMAKE_CURRENT_SOURCE_DIR}/jpeglib
		${CMAKE_CURRENT_SOURCE_DIR}/libpng)
target_compile_definitions(Irrlicht PRIVATE
	IRRLICHT_EXPORTS=1
	$<$<CONFIG:Debug>:_DEBUG>)
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
	target_compile_options(Irrlicht PRIVATE
		$<$<COMPILE_LANGUAGE:CXX,OBJCXX>:-Wall>
		$<$<COMPILE_LANGUAGE:CXX,OBJCXX>:-pipe>
		$<$<COMPILE_LANGUAGE:CXX,OBJCXX>:-fno-exceptions>
		$<$<COMPILE_LANGUAGE:CXX,OBJCXX>:-fno-rtti>
		$<$<COMPILE_LANGUAGE:CXX,OBJCXX>:-fstrict-aliasing>)
	include(CheckCXXCompilerFlag)
	check_cxx_compiler_flag(-Wno-template-id-cdtor IRR_HAS_NO_TEMPLATE_ID_CDTOR)
	if(IRR_HAS_NO_TEMPLATE_ID_CDTOR)
		target_compile_options(Irrlicht PRIVATE
			$<$<COMPILE_LANGUAGE:CXX>:-Wno-template-id-cdtor>)
	endif()
	if(IRR_PROFILE)
		target_compile_options(Irrlicht PRIVATE $<$<COMPILE_LANGUAGE:CXX>:-pg>)
		target_link_options(Irrlicht PUBLIC -pg)
	endif()
set_target_properties(Irrlicht PROPERTIES
	POSITION_INDEPENDENT_CODE ON
	VERSION	 ${PROJECT_VERSION}
	SOVERSION ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR})
endif()
if(IRR_LEGACY_OUTPUT_DIRS)
	if(WIN32)
		set(_irr_system Win32-gcc)
	elseif(APPLE)
		set(_irr_system MacOSX)
	else()
		set(_irr_system Linux)
	endif()
	set_target_properties(Irrlicht PROPERTIES
		ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib/${_irr_system}
		LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib/${_irr_system}
		RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin/Win32-gcc)
endif()
if(WIN32)
	target_link_libraries(Irrlicht PRIVATE gdi32 opengl32 winmm)
	target_sources(Irrlicht PRIVATE CD3D9RenderTarget.cpp)
	target_compile_definitions(Irrlicht PRIVATE
		NO_IRR_COMPILE_WITH_DIRECTINPUT_JOYSTICK_ _MBCS)
	if(BUILD_SHARED_LIBS)
		target_compile_definitions(Irrlicht PRIVATE _USRDLL)
	else()
		target_compile_definitions(Irrlicht PUBLIC _IRR_STATIC_LIB_)
	endif()
	if(IRR_USE_DX9)
		target_compile_definitions(Irrlicht PRIVATE IRR_COMPILE_WITH_DX9_DEV_PACK)
		if(MINGW)
			target_link_libraries(Irrlicht PRIVATE d3dx9d)
		endif()
	else()
		target_compile_definitions(Irrlicht PRIVATE NO_IRR_COMPILE_WITH_DIRECT3D_9_)
	endif()
	if(MINGW)
		target_compile_definitions(Irrlicht PRIVATE __GNUWIN32__ WIN32 _WIN32 _WINDOWS)
		if(BUILD_SHARED_LIBS)
			target_link_options(Irrlicht PRIVATE -Wl,--add-stdcall-alias)
			set_target_properties(Irrlicht PROPERTIES PREFIX "")
		endif()
	endif()
elseif(APPLE)
	if(EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/MacOSX/CIrrDeviceMacOSX.mm)
		target_sources(Irrlicht PRIVATE
			MacOSX/CIrrDeviceMacOSX.mm
			MacOSX/OSXClipboard.mm
			MacOSX/AppDelegate.mm)
		target_include_directories(Irrlicht PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/MacOSX)
	else()
		message(WARNING "Irrlicht: MacOSX/ not found.")
	endif()
	target_link_libraries(Irrlicht PRIVATE
		"-framework Cocoa" "-framework IOKit" "-framework OpenGL")
else()
	find_package(OpenGL REQUIRED)
	find_package(X11 REQUIRED)
	if(NOT X11_Xxf86vm_FOUND)
		message(FATAL_ERROR "Irrlicht needs the XFree86-VidMode library.")
	endif()
	target_link_libraries(Irrlicht PRIVATE OpenGL::GL X11::X11 X11::Xxf86vm)
endif()
install(TARGETS Irrlicht
	ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
	LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
	RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/
	DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/irrlicht
	FILES_MATCHING PATTERN "*.h")
