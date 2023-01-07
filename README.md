# Dynamic-HTML-Custom-Multi-purpose-slider-Arrow-Navigation-with-jQuery
Dynamic HTML Custom Multi-purpose slider Arrow Navigation with jQuery

```JS

   /**
   * Cooked by nielsoffice
   **/
    var childCountList         = 1; // select second child which array 1
    var parentContainerSlider  = jQuery('#slider'); // select parent container
    var parentContainerListTag = jQuery('.slides'); // select slider container
    var childListTags          = '.slides li';      // select slider child
    var childListTagsActive    = '.slides li.active';  // select slider child active
   
    jQuery(() => {

        const performSlides = jQuery.fn.sliderDynamicPost = function() { 

             let childFirst = jQuery( childListTags ).first().show('fast',function() { 
        
             jQuery( this ).addClass('active');  

             if( jQuery( childListTags ).first().hasClass('active') === true ) {

                    let __sliders   = jQuery(childListTags).length;
                    let __leftIcon  = jQuery('#leftIcon');
                    let __rightIcon = jQuery('#rightIcon');

                    if( jQuery( parentContainerListTag ).find('li').hasClass('active') ) {

                    const sliderPushRight = ( rightTurn = true) => {

                        let __counts = childCountList++;  
                        if( __counts >= __sliders ) { 
                            
                            const currentEstate = ( jQuery( childListTags ).first().hasClass('active') ) ? 1 : 0 ; 
                            childCountList      = currentEstate;  
                            __counts            = childCountList++; 

                        }

                        if(rightTurn) {
                           
                            setTimeout(function() {

                                jQuery(childListTagsActive).next().show(() => {

                                jQuery(childListTagsActive).prev().hide().removeClass('active');

                                }).addClass('active');

                            });
       
                        }

                        jQuery(childListTagsActive).hide().removeClass('active');
                        jQuery(childListTags).eq( __counts ).show().addClass('active');
                  
                    };  
                    
                    var childCountList  = ( __sliders );  

                    const sliderPushLeft = ( leftTurn = true ) => {

                        let __counts = --childCountList;  
                        let __count  = Math.abs(__counts);
                        if( __count  > __sliders ) { childCountList = __sliders  ; __counts = --childCountList; } 

                        jQuery(childListTagsActive).hide().removeClass('active');
                        jQuery(childListTags).eq( __counts ).show().addClass('active');

                    }; 

                     const $__thisEstate = jQuery( parentContainerListTag ).find('li').hasClass('active') ? true : false;

                    __leftIcon.on('click', () => { sliderPushLeft( $__thisEstate ); });
                    __rightIcon.on('click', () => { sliderPushRight( $__thisEstate ); }); 

                }
             } 
          }); 
        };

      performSlides();
        
    });

```
