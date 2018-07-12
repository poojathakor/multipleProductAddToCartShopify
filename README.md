# multipleProductAddToCartShopify
Hello, By using this code, You will be able to add multiple variant of products with varied quantity into the cart, Used Shopify, Timber theme, Hope You Like it

theme is attached, will only run in **Shopify store**.

Go through following **screenshots**
1) http://prntscr.com/k5kun9
2) http://prntscr.com/k5kv8k
3) http://prntscr.com/k5kvgq
4) http://prntscr.com/k5kvw1

```
jQuery(function($) {
    
    $('#AddToCart').click(function(){
      var i = 1;
      var checkedArray = new Array();
      var Qty = new Array();
      var checkedSize = $('#productSelect .checkbox_cls').size();
      //       alert($('#pro2 .checkbox_cls').attr('data-id'));
      for(i=0;i< checkedSize ; i++)
      {
        if($('#pro'+(i+1)+' .checkbox_cls').is(":checked"))
        {
          var getChecked =  $('#pro'+(i+1)+' .checkbox_cls').attr('data-id');
          checkedArray.push(getChecked);
          var QtyChecked =  $('#pro'+(i+1)+' .input').val();
          Qty.push(QtyChecked);
        }
        else{
          console.log("else");
        }
        
      }
      
		console.log(checkedArray);
        console.log(Qty);
      for(var i=0 ; i < checkedArray.length;i++ ){
        
       
        if($('#pro'+(i+1)+' .checkbox_cls').is(":checked"))
        {
          var QtyChecked =  $('#pro'+(i+1)+' .input').val();
        }
        else{
          console.log("else");
        }
         itemId = checkedArray[i];
      var data_ajax = {
          quantity:QtyChecked,
          id: itemId
        }

      
       var params = {
          type: 'POST',
          url: '/cart/add.js',
          data: data_ajax,
          dataType: 'json',
          async:false,
          success: function(line_item) {
                        console.log("successfully added");
          },
          error: function(er) {
            var err = $.parseJSON(er.responseText);
            return false;
             
          }
        }
        
        $.ajax(params);
      
      }
      ajaxCart.load();
    });
   
  });

```
