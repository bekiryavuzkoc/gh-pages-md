---
title: Create Wiseplayer and Play Video
description: 15
---

**1. Locate following line to create the Wise Player Factory instance in
WisePlayerInit Object.**

<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    //TODO Initializing of Wise Player Factory
<cite class="pln">
</cite></code></pre>

       //TODO Initializing of Wise Player Factory

**2. Create the Wise Player Factory instance**

<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    val factoryOptions = WisePlayerFactoryOptions.Builder().setDeviceId("xxx").build()
    // In the multi-process scenario, the onCreate method in Application is called multiple times.
    // The app needs to call the WisePlayerFactory.initFactory() API in the onCreate method of the app process (named "app package name") 
    // and WisePlayer process (named "app package name:player").
    WisePlayerFactory.initFactory(context, factoryOptions, object : InitFactoryCallback {
        override fun onSuccess(factory: WisePlayerFactory) {
            wisePlayerFactory = factory
        }
        override fun onFailure(errorCode: Int, msg: String) {
            Log.d("WisePlayerInit", "onFailure: $errorCode - $msg")
        }
    })
<span class="pln">
</span></code></pre>

        val factoryOptions = WisePlayerFactoryOptions.Builder().setDeviceId("xxx").build()
        // In the multi-process scenario, the onCreate method in Application is called multiple times.
        // The app needs to call the WisePlayerFactory.initFactory() API in the onCreate method of the app process (named "app package name") 
        // and WisePlayer process (named "app package name:player").
        WisePlayerFactory.initFactory(context, factoryOptions, object : InitFactoryCallback {
            override fun onSuccess(factory: WisePlayerFactory) {
                wisePlayerFactory = factory
            }
            override fun onFailure(errorCode: Int, msg: String) {
                Log.d("WisePlayerInit", "onFailure: $errorCode - $msg")
            }
        })
        
        


<p>Description of <strong>Wise Player Factory</strong> is as following:<br></p>
<table style="width: 100%;table-layout: fixed;">
	<tbody><tr></tr>
	<tr><td colspan="1" rowspan="1"><p>Parameter</p>
	</td><td colspan="1" rowspan="1"><p>Type:</p>
	</td><td colspan="1" rowspan="1"><p>Mandatory or Not</p>
	</td><td colspan="1" rowspan="1"><p>Description</p>
	</td></tr>
	<tr><td colspan="1" rowspan="1"><p>context</p>
	</td><td colspan="1" rowspan="1"><p>Context</p>
	</td><td colspan="1" rowspan="1"><p>M</p>
	</td><td colspan="1" rowspan="1"><p>Android context object, which is not set to null.</p>
	</td></tr>
	<tr><td colspan="1" rowspan="1"><p>options</p>
	</td><td colspan="1" rowspan="1"><p>Integer</p>
	</td><td colspan="1" rowspan="1"><p>M</p>
	</td><td colspan="1" rowspan="1"><p>Instance of the WisePlayer factory class initialization option <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-References-V5/wpf-options-0000001050439397-V5" target="_blank">WisePlayerFactoryOptions</a></p>
	</td></tr>
	<tr><td colspan="1" rowspan="1"><p>callback</p>
	</td><td colspan="1" rowspan="1"><p>Object</p>
	</td><td colspan="1" rowspan="1"><p>M</p>
	</td><td colspan="1" rowspan="1"><p>Instance of the <a href="https://developer.huawei.com/consumer/en/doc/HMSCore-References-V5/init-factory-callback-0000001050199187-V5" target="_blank">InitFactoryCallback API</a> for initializing the WisePlayer factory class.</p>
	</td></tr>
</tbody></table>
**3. Locate following line and set the EditTexts Urls in MainActivity to
play related buttons**

       // TODO Set video Url or Urls

**4.Set the EditTexts Urls**

     edtUrl.setText(resources.getString(R.string.single_url))
     edtMultipleUrl.setText(resources.getString(R.string.multiple_url))


**5. Locate following line and create Wise Player Instance in
WisePlayerInit Object.**

      // TODO Initializing of Wise Player Instance

**6. Create Wise Player Instance**

      return wisePlayerFactory.createWisePlayer()

**Note: Frame Layout is necessary for SurfaceView to display videos,
otherwise only audio will be listened**

<br><img style="width: 400.00px" src="https://raw.githubusercontent.com/bekiryavuzkoc/testRepo/gh-pages/assets/framelayout.PNG" onclick="imageclick(src)">

**7. Locate following line in Play Activity.**

      //TODO Setting the Listeners

**8. Set listeners in Play Activity.**

      player.setReadyListener(this)
      player.setErrorListener(this)
      player.setEventListener(this)
      player.setResolutionUpdatedListener(this)
      player.setLoadingListener(this)
      player.setPlayEndListener(this)
      player.setSeekEndListener(this)


**9. Locate following line in Play Activity.**

     //TODO Callback Listener

**10. Set the Callback Listener in Play Activity.**

      surfaceView.holder.addCallback(this)

**11. Locate following line in Play Activity.**

     //TODO Callback Listener

**12. Set the Seekbar Listener in Play Activity.**

      seekBar.setOnSeekBarChangeListener(this)

**13. Locate following line in Play Activity.**

      //TODO Starting the Player


**14. Start Wise Player in Play Activity.**

      player?.start()

**15. Locate following line in Play Activity.**

      //TODO Surface Change

**16. Set surface change to Wise Player.**

      player.setSurfaceChange()

**17. Locate following line in Play Activity.**

      //TODO Surface Destroy

**18. Suspend the Wise Player if surface is destroyed.**

      player.suspend()

**19. Locate following line in Play Activity.**

      //TODO Surface Create

**20. Resume Wise Player with the current time when app is sent to
foreground.**

      player.setView(surfaceView)
      player.resume(PlayerConstants.ResumeType.KEEP)

**21. Locate following line in Play Activity.**

      //TODO Release Wise Player

**22. Release Wise Player and listeners in Play Activity.**

      player.setErrorListener(null)
      player.setEventListener(null)
      player.setResolutionUpdatedListener(null)
      player.setReadyListener(null)
      player.setLoadingListener(null)
      player.setPlayEndListener(null)
      player.setSeekEndListener(null)
      player.release()



