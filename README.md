
function run(){
	$('#generate').click(function(){

		var form = {
			numbers:$('#numbers').val(),
			min:$('#min').val(),
			max:$('#max').val(),
			columns:$('#columns').val(),
			order:$('#order').val(),
			unique:$('#unique').is(':checked'),
		};

		$(document).ajaxStart(function(){
			$('#generate').attr('disabled',true);
		});

		$(document).ajaxStop(function(){
			$('#generate').attr('disabled',false);
		});

		$.ajax({type:'post', data:form, url:'/ajax/random-number.php', dataType:'json',
			success: function(j){
				$('#result').html(j.result);
			}
		});
	});
}
