---
title: Advanced Features
description: 5
---

<ol type="1">
  <li><h3>MLBcrCaptureConfig.Factory :</h3></li>
  <p>With the object of MLBcrCaptureConfig, you can Specify the expected result type of bank card recognition.</p>
  
<p><strong>1.1. Locate following line for MLBcrCaptureConfig.Factory custom configurations.</strong></p>
<pre><div id="copy-button33" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  // TODO : custom initialize of MLBcrCaptureConfig.Factory
</code></pre>
<p><strong>1.2. Implement the Wise Player’s seek method.</strong></p>
<pre><div id="copy-button34" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>  val config = MLBcrCaptureConfig.Factory()
            // Set the expected result type of bank card recognition.
            // MLBcrCaptureConfig.RESULT_NUM_ONLY: Recognize only the bank card number.
            // MLBcrCaptureConfig.RESULT_SIMPLE: Recognize only the bank card number and validity period.
            // MLBcrCaptureConfig.ALL_RESULT: Recognize information such as the bank card number, validity period, issuing bank, card organization, and card type.
            .setIsShowPortraitStatusBar(true)
            .setResultType(MLBcrCaptureConfig.RESULT_ALL)
            // Set the recognition screen display orientation.
            // MLBcrCaptureConfig.ORIENTATION_AUTO: adaptive mode. The display orientation is determined by the physical sensor.
            // MLBcrCaptureConfig.ORIENTATION_LANDSCAPE: landscape mode.
            // MLBcrCaptureConfig.ORIENTATION_PORTRAIT: portrait mode.
            .setOrientation(MLBcrCaptureConfig.ORIENTATION_AUTO)
            .create()
<span class="pln">
</span></code></pre>

 <li><h3>MLBcrCaptureResult content details:</h3></li>
 <p>With the object of MLBcrCaptureResult, you can get recognised card details.</p>

<p><strong>2.1.Set views with MLBcrCaptureResult object detail information in displaySuccessAnalyseResults function to show recognised card details</strong></p>
<pre><div id="copy-button13" class="copy-btn" title="Copy" onclick="copyCode(this.id)"></div><code>    private fun displaySuccessAnalyseResults(result: MLBcrCaptureResult) {
        val analyseResults: String = editFormatCardAnalyseResult(result).toString()
        Log.i(TAG, "Success AnalyseResults : $analyseResults")
        Utils.createVibration(applicationContext, 200)
        clResults.visibility = View.VISIBLE
        ivDelete.visibility = View.VISIBLE
        ivCardImage.setImageBitmap(result.originalBitmap)
        ivCardNumberImage.setImageBitmap(result.numberBitmap)
        tvCardType.text = result.organization
        tvExpireDate.text = result.expire
        tvCardNumberAll.text = result.number
        tvCardNumber1.text = result.number.substring(0, 4)
        tvCardNumber2.text = result.number.substring(4, 8)
        tvCardNumber3.text = result.number.substring(8, 12)
        tvCardNumber4.text = result.number.substring(12, 16)
    }
 <span class="pln">
</span></code></pre>
</ol>
