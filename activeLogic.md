# Активная логика

Элемент позволяет подключить на страницу исполняемый скрипт, т.е. предназначен для выбора и вставки нужного php-файла.

## Входные параметры:

Входных параметров нет.

## Тело чанка

В столбце `body` лежит JavaScript код.

## Пример JavaScript кода

На странице пользователя вставится такой код:

```javascript
<script>
$(document).ready(function(){
  $.post('/active/ajax.php',{'get_tovar_by_otrasl':1,'otrasl':4},function(response){
    if (response.status!='ok') {
      return 0;
    }
if(response.html){
    $('#main_tovar').html(response.html);
}else{
    <user:!administrator>
    $('#main_tovar').append('<div class="dob"><p style="padding-top: 26px; margin: 0px 25% 56px;">В данной категории еще нет товаров</p>'+
    '<user:registered><a href="21.html#5" class="btn_dob"></a></user:registered>'+
    '<user:unregistered><a href="23.html" class="btn_dob"></a></user:unregistered><br></div>');
    </user:!administrator>
    <user:administrator>
    $('#main_tovar').append('<div class="dob" style="background-image: none;"><p style="padding-top: 26px; margin: 0px 25% 56px;">В данной категории еще нет товаров</p></div>');
    </user:administrator>

}
$('.block_product').hover(function(){
$(this).find('.expert_top').show();
},function(){
$(this).find('.expert_top').hide();
});
  },'json');
});
</script>
<div id="main_tovar"></div>
```
