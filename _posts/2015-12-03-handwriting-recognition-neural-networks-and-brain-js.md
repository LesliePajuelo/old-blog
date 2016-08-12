---
id: 228
title: Handwriting recognition, neural networks, and Brain.JS
date: 2015-12-03T15:56:00+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=228
permalink: /handwriting-recognition-neural-networks-and-brain-js/
dsq_thread_id:
  - 4372468537
categories:
  - HackReactor
  - neural network
---
### tl;dr Over 3 full work days a friend and I built an interface which recognizes numbers by using a neural network. <a href="https://numeral-net.herokuapp.com/" target="_blank">Numeral-Net.herokuapp.com</a>

## Neural Networks and Machine Learning

There are a lot of great articles explaining what they are. At its core it&#8217;s computers taking in vast quantities of input information, comparing it, and making predictions. Right now neural networks detect some <a href="http://www.ijcaonline.org/journal/number26/pxc387783.pdf" target="_blank">cancers better than radiologists</a>, have <a href="http://www.cbronline.com/news/verticals/the-boardroom/housetrip-ceo-taking-on-airbnb-with-neutral-networks-4740454" target="_blank">business based on them</a>, <a href="http://neuroph.sourceforge.net/tutorials/FaceRecognition/FaceRecognitionUsingNeuralNetwork.html" target="_blank">facial recognition</a>, <a href="http://scitation.aip.org/content/aip/journal/jcp/131/7/10.1063/1.3206326" target="_blank">quantum chemistry</a> and much more.  The most powerful applications for them are tasks which are normally seen as easy for people and difficult for computers, such as Google training one to <a href="http://www.wired.com/2012/06/google-x-neural-network/" target="_blank">recognize cat videos.</a> The difficulty of these task are that the rules for success are not clear to the programmers. So the training of a neural network is acquisition of rules to follow. But, it&#8217;s still on computers that at some point need to have everything represented as numbers.

## Quick Basics &#8211; pictures from <a href="http://neuralnetworksanddeeplearning.com" target="_blank">neural networks and deep learning. com</a>

[<img class="alignleft wp-image-230 size-full" src="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/1.png?fit=487%2C270" alt="4 layer neural network with notes about how small changes in the weights have small changes in the output" srcset="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/1.png?w=487 487w, http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/1.png?resize=300%2C166 300w" sizes="(max-width: 487px) 100vw, 487px" data-recalc-dims="1" />](http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/1.png)

There is a lot of terminology in the world of neural networks, and neurons which have a range of values are called sigmoids. If they were simpler and had either a value of 0 or 1 they&#8217;d be called perceptons. However, a sigmoid allows for small differences in the input layers to have appropriately small changes on the output layer. They type of learning our network did is supervised learning. Meaning that we input a lot of data and told the network what it was. Adjustments are made with each new input and each layer to closely &#8220;learn&#8221; what the correct given answer is.

The other two main types are unsupervised learning, which is good for when there is a lot of data and no known end result. And Reinforcement Learning when certain goals are given but to allow the computer to find it&#8217;s way there. It&#8217;s used mostly in robotics. Like in this <a href="https://www.ted.com/talks/hod_lipson_builds_self_aware_robots?language=en" target="_blank">TED talk where robots learn to walk.</a>

&nbsp;

&nbsp;

## What we did

[<img class="alignleft wp-image-231 size-full" src="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/2.png?fit=597%2C324" alt="Depiction of our neural network with 784 input neurans and 2 hidden layers with 396, 192 nuerons each with an output of 10 neurons" srcset="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/2.png?w=597 597w, http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/2.png?resize=300%2C163 300w" sizes="(max-width: 597px) 100vw, 597px" data-recalc-dims="1" />](http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/12/2.png) Our network took in <a href="http://yann.lecun.com/exdb/mnist/" target="_blank">MNIST images</a> which are in the IDX format which is &#8220;a simple format for vectors and multidimensional matrices&#8221;. In other words a challenge to extract. Each image is 28px x 28px and each pixel has a value of between 0 to 255.

28&#215;28 is where the 784 neurons come from. Which moving away from neural network-speak is an array with 784 values.

Math is done between each layer converting the 0-255 into values of between 0-1. It compares the differences between what it has learned before for that type of digit, adjusts what it thinks that digit should look like at that stage. Passes that data forward to a pre-classification of 392 labels, 196 labels and finally an array of 10 each of which represent a digit.

The final array looks like: `[0.00154, 0.97021, 0.21351, 0.03350, 0.03212, 0.32897, 0.34197, 0.62130, 0.02154, 0.43215]` for the number one.
  
We used <a href="https://github.com/harthur/brain" target="_blank">brain.js</a> to create and use our neural network as it had the most understandable code base. Once the MNIST data had been converted from it&#8217;s idx format to a CSV file it was just a matter of iterating through that file to push everything into a single array.
  
It uses a callback to assure that our trainDataArray is fully populated before getting ran through

<pre class="theme:sublime-text lang:js decode:true"><code>fs.readFile(process.cwd() + '/assets/mnist_train.csv', function(err, data) {
  if(err) {
    throw err;
  } else {
    var csvData = data.toString().split("\n");
    for(var i = 0; i &lt; 59999; i++) {
      trainDataArray.push(csvData[i].split(','));
    }
    
  trainBrain(trainDataArray);
  
  var endTime = new Date() - startTime;
  console.log('Training took ' + endTime / 1000 +'s');
 }
});</code></pre>

Another callback which stays open for between seconds and hours depending how large the trainDataArray is. Using all of the training data it took my computer 2.5 hours and my partner 1.25 hours to process.

<pre class="crayon-selected"><code>var trainBrain = function(data) {
  var labels;
  var pictures;
  var TrainingData = [];
  data.forEach(function(arr) {
    // Use position of 1 in output as label equivalent:
    var output = Array
                .apply(null, Array(10))
                .map(Number.prototype.valueOf, 0); 
    labels = parseInt(arr.shift());
    output[labels] = 1;

    pictures = arr.map(function(num){ return parseInt(num) } );
    
    TrainingData.push( { input: pictures, output: output } );
  });

  net.train(TrainingData, {
    log: true,
    logPeriod: 1,
    errorThresh: 0.025,
    learningRate: 0.1,
    iterations: 20
  });

  json = JSON.stringify(net.toJSON());
  fs.writeFile(process.cwd() + '/assets/fourthBrainData.json', json, function(err){
    if(err) {
      throw err;
    }
  });
  console.log('training...');
};</code></pre>

Log and log period console log at the end of each epoch, or run through the data, the errorThreshold is how low the error must be for the loop to end and the final neural network to be written to filed. Iterations is the cap of how many runs through the data it&#8217;ll do. Something we noticed earlier was that depending on the settings it would oscillate around a value and even letting it keep trying it will not advance further. The learning rate is what can lead to overfitting. The default is set to 0.3 and we dialed it down a little but going too far would make a neural network that essentially memorizes the input data but cannot generalize well for new data.

The error is cumulative sum of the training at each point which is divided by number of items in the input array.

    var error = mse(this.errors[this.outputLayer]);
    

Each individual error is calculated using mean square error

    function mse(errors) {
      var sum = 0;
      for (var i = 0; i < errors.length; i++) {
        sum += Math.pow(errors[i], 2);
      }
      return sum / errors.length;
    }
    
    And that errors arrays is calculated for each node in each layer.
    Where k iterate through all the possible deltas. Delta being the difference between each node and the ideal value for that node.
    <code> error += deltas[k] * this.weights[layer + 1][k][node];
    </code>

The end result of this was a 26MB file with an object with a hash of 1382 sigmoids. To actually use this neural network it needs to be fed an array of 784 values
  
fromJSON un-hashes the file, compares each value with its corresponding value on the input layer and calculates the differences times the weights for each one.

    var trainedNetwork = function(data, cb) {
      net.fromJSON(currentBrain);
    
      var results = net.run(data);
      if (results) {
          cb(results);
        } else {
          console.error('No results from trained Network!');
        }
    
    };

To pass it that data array we used express and an AJAX call.

<pre>app.route('/trainedNetwork')
    .post(function(req, res) {
      brainTrain.trainedNetwork(req.body['input[]'], function(data) {
        console.log('CB success! Data sent: ', data);
        res.send(data);
      });
    })
</pre>

    function() {
        $.ajax({
          type: 'POST', 
          url:'/trainedNetwork',
          data: {
            input: redValues
          },
          success: function(data){
            renderResults(data)
          }
        })
      })

Now the tricky part. Converting a 280 x 280 canvas into the right format. There are several way to do this. All of which &#8220;work&#8221; but not quite right. The one we had the most success with was with redrawing our full size image to a 20,20 space on the large canvas and then creating a duplicate small canvas. We then pulled out the red pixels as the image data is RGBA it is simply the first value. Another method we could have done was to sum and average. The resulting array for a number one looks very much like a number one in the MNIST data but it is off center. So more jiggering with this part is still needed.

    var image = context.getImageData(0,0,canvas.width, canvas.height)
      var shadowCanvas = document.createElement('canvas');
      var shadowContext = shadowCanvas.getContext('2d');
      shadowCanvas.width = 28;
      shadowCanvas.height = 28;
    
      shadowContext.drawImage(canvas, 0,0,280,280,4,4,20,20);
      document.body.appendChild(shadowCanvas);
      var teeny = shadowContext.getImageData(0,0,shadowCanvas.width, shadowCanvas.height)
    
      // Pull out red pixels:
      var redValues = [];
      for(var i = 0; i < teeny.data.length; i = i + 4) {
        redValues.push(teeny.data[i]);
      }
    

## Challenges

Extracting IDX data was the biggest. It is is a binary data format, after several failed attempts we googled harder and found that there were CSV files for it. Thank you <a href="http://pjreddie.com/projects/mnist-in-csv/" target="_blank">Joseph Redmon</a>.

Most of our time was eaten up by the above function. How to convert canvas element into the right format. Had we figured this out a day sooner we would have been able to pull brain.js out. The best answer we found was just from pouring over the mdn docs and experimenting. Thank you <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank">mdn.io</a>. Also, to anyone else, pulling out the <a href="https://developer.mozilla.org/en-US/docs/Web/API/ImageData" target="_blank">ImageData</a> and trying to average and condense that array is the rabbit hole which seemed the most promising and produced the worst results.