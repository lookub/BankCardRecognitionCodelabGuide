---
title: Create MLBcrCaptureConfig and MLBcrCapture
description: 15
---
<p><strong>1. Locate following line to create and initialize the MLBcrCapture.Callback Object.</strong></p>
<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    // TODO : create and initialize of MLBcrCapture.Callback 
<span class="pln">
</span></code></pre>
<p><strong>2. Create and initialize of MLBcrCapture.Callback</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>bcrCaptureCallback = object : MLBcrCapture.Callback {
            override fun onSuccess(result: MLBcrCaptureResult) {
                if (result == null) {
                    Log.e(TAG, "callback MLBcrCaptureResult is null")
                    return
                }
                Log.i(TAG, "Success AnalyseResults : $result")
            }
            override fun onCanceled() {
                Log.d(TAG, "MLBcrCaptureResult callback onCanceled !")
            }
            override fun onFailure(retCode: Int, bitmap: Bitmap) {
                Log.d(TAG, "MLBcrCaptureResult callback onFailure ! $retCode")
            }
            override fun onDenied() {
                Log.d(TAG, "MLBcrCaptureResult callback onCameraDenied !")
            }
        }
    }
<span class="pln"></span></code></pre>
<p><strong>3. Locate following line to create the MLBcrCaptureConfig.Factory Object.</strong></p>
<pre><div id="copy-button10" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    // TODO : create and initialize of MLBcrCaptureConfig.Factory
<span class="pln">
</span></code></pre>
<p><strong>4. Create and initialize of MLBcrCaptureConfig.Factory</strong></p>
<pre><div id="copy-button11" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>         val config = MLBcrCaptureConfig.Factory()
            // Set the expected result type of bank card recognition.
            .setIsShowPortraitStatusBar(true)
            .setResultType(MLBcrCaptureConfig.RESULT_ALL)
            .setOrientation(MLBcrCaptureConfig.ORIENTATION_AUTO)
            .create()
<span class="pln"></span></code></pre>
<p><strong>5. Locate following line and create MLBcrCaptureFactory.getInstance().getBcrCapture with setted Config</strong></p>
<pre><div id="copy-button12" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>   // TODO : create and initialize of MBcrCapture 
<span class="pln">
</span></code></pre>
<p><strong>6.Create and initialize of MLBcrCaptureFactory.getInstance().getBcrCapture(config)</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>        try {
            val bcrCapture = MLBcrCaptureFactory.getInstance().getBcrCapture(config)
            bcrCapture.captureFrame(this, bcrCaptureCallback)
        } catch (e: Exception) {
            Log.e(TAG, "MLBcrCapture captureFrame Exception : " + e.message, e)
            displayFailureAnalyseResults(e.message.toString())
        }
 <span class="pln">
</span></code></pre>
<p><strong>7.Invoke checkAndRequestPermissions function when click the R.id.ivCardImage, R.id.btnTakePhoto buttons</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
        // TODO : call ActivityCompat.requestPermissions with checkAndRequestPermissions method
    private fun checkAndRequestPermissions() {
        ActivityCompat.requestPermissions(
            this,
            permissionRequestCameraAndStorage,
            permissionCodeCameraAndStorage
        )
    }
 <span class="pln">
</span></code></pre>
<p><strong>8.Invoke startMLBcrCaptureCameraStream function if permissions were has got granted in onRequestPermissionsResult method</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
        // TODO : call startMLBcrCaptureCameraStream function if permissions were has got granted
    override fun onRequestPermissionsResult(
        requestCode: Int,
        permissions: Array<String?>,
        grantResults: IntArray
    ) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults)
        Log.d(TAG, "PermissionsResult : requestCode : $requestCode")
        if (requestCode == permissionCodeCameraAndStorage) {
            if (grantResults.isNotEmpty() && grantResults[0] == PackageManager.PERMISSION_GRANTED && grantResults[1] == PackageManager.PERMISSION_GRANTED
            ) {
                startMLBcrCaptureCameraStream()
            } else {
                Log.e(TAG, "onRequestPermissionsResult : CameraPermission  was NOT GRANTED")
            }
        }
    }
 <span class="pln">
</span></code></pre>
<p><strong>9.Invoke displaySuccessAnalyseResults function to show recognised card details</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
        // TODO : call displaySuccessAnalyseResults method with MLBcrCaptureResult param in Callback onSuccess
        // to show recognised card details
        displaySuccessAnalyseResults(result)
 <span class="pln">
</span></code></pre>
<p><strong>10.In the camera stream screen that pops up, place the card in the frame.</strong></p>
<aside class="special">
<p><strong>Note: Once recognition is successful, you will see the following changes on the main screen : </strong></p>
</aside>
<center>
<img style="width: 400.00px " src="../assets/ss.jpg" onclick="imageclick(src)">
</center>
<p><strong>11.Invoke copyTextToClipboard function with view param when click the R.id.tvCardNumberAll or click other textViews thats are showing recognised card numbers partially</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>
        // eg : copyTextToClipboard(tvCardNumberAll)
        // 
        // TODO : use Context.CLIPBOARD_SERVICE and set clipboard.setPrimaryClip with created ClipData.newPlainText object
        private fun copyTextToClipboard(clickedView: TextView) {
          val clickedText: String = clickedView.text.toString()
          val clipboard = applicationContext.getSystemService(Context.CLIPBOARD_SERVICE) as ClipboardManager
          val clip = ClipData.newPlainText("copiedCardNumber", clickedText)
          clipboard.setPrimaryClip(clip)
        }
 <span class="pln">
</span></code></pre>