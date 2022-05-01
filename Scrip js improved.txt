// Player name
var player1 = "Player 1";
var globalSteps = [
	{
		"step": 1,
		"direction": "right",
		"question": null
	},
	{
		"step": 1,
		"direction": "down",
		"question": {
			"q": "Who is the prime minister in India?",
			"o1": "Naredra Modi",
			"o2": "Indira Gandhi",
			"o3": "Atal Bihari Bajpayi",
			"o4": "Rajiv Gandhi",
			"correct": 1
		}
	},
	{
		"step": 2,
		"direction": "right",
		"question": null
	},
	{
		"step": 1,
		"direction": "down",
		"question": null
	},
	{
		"step": 1,
		"direction": "left",
		"question": null
	},
	{
		"step": 3,
		"direction": "down",
		"question": null
	},
	{
		"step": 1,
		"direction": "right",
		"question": null
	},
	{
		"step": 2,
		"direction": "up",
		"question": null
	},
	{
		"step": 3,
		"direction": "right",
		"question": null
	},
	{
		"step": 1,
		"direction": "down",
		"question": null
	},
	{
		"step": 1,
		"direction": "left",
		"question": null
	},
	{
		"step": 2,
		"direction": "down",
		"question": null
	},
	{
		"step": 1,
		"direction": "right",
		"question": null
	}
];	
var gIndex = 0;
	
	// Function to change the player name
	function editNames() {
		player1 = prompt("Change Player1 name");
		document.querySelector("p.Player1").innerHTML = player1;
	}

	// Function to roll the dice
	function rollTheDice() 
	{
		var randomNumber1 = Math.floor(Math.random() * 6) + 1;
		document.querySelector(".img1").setAttribute("src",	"img/dice" + randomNumber1 + ".png");
		animateTheCat(gIndex, randomNumber1);		
	}
	function animateTheCat(index, diceNumber)
	{
		var cat = $(".img-temper");
		var top 	= parseInt(cat.css("top"));
		var left 	= parseInt(cat.css("left"));
		var curStatus = globalSteps[index];
		if(curStatus.direction == "down")
		{
			if(diceNumber <= curStatus.step)
			{
				for(var i = 0; i < curStatus.step; i++)
					top = top + 45;
				
				if(curStatus.question != null)
				{
					$(".que").html(curStatus.question.q);
					$(".option1").html("<input type='radio' name='answer' id='option1' valie='o1'/> <label for='option1'>" + curStatus.question.o1 + "</label>");
					$(".option2").html("<input type='radio' name='answer' id='option2' valie='o1'/> <label for='option2'>" + curStatus.question.o2 + "</label>");
					$(".option3").html("<input type='radio' name='answer' id='option3' valie='o1'/> <label for='option3'>" + curStatus.question.o3 + "</label>");
					$(".option4").html("<input type='radio' name='answer' id='option4' valie='o1'/> <label for='option4'>" + curStatus.question.o4 + "</label>");
					$("#exampleModal").modal("show");
					
					
				}
				gIndex++;
				
			}
		}
		else if(curStatus.direction == "right")
		{
			if(diceNumber <= curStatus.step)
			{
				for(var i = 0; i < curStatus.step; i++)
					left = left + 45;
				gIndex++;
			}
		}
		else if(curStatus.direction == "left")
		{
			if(diceNumber <= curStatus.step)
			{
				for(var i = 0; i < curStatus.step; i++)
					left = left - 45;
				gIndex++;
			}
		}
		else if(curStatus.direction == "up")
		{
			if(diceNumber <= curStatus.step)
			{
				for(var i = 0; i < curStatus.step; i++)
					top = top - 45;
				gIndex++;
			}
		}
		cat.css("top", top+"px");
		cat.css("left", left+"px");
	}