//Retrieve Player Variables
var player = GetPlayer();
userNotes = player.GetVar("Notes");
userScore = player.GetVar("Score");

//Create PDF
var doc = new jsPDF('landscape');

//Create Split Text Variable
var splitNotes = doc.splitTextToSize(userNotes, 550);

//Color Rectangle at top
doc.setFillColor(51, 204, 255);
doc.rect(0, 0, 1700, 50, 'F');

//Congrat Text
doc.setFontSize(36);
doc.setFont("helvetica");
doc.setFontStyle("bold");
doc.setTextColor(255, 255, 255);
doc.text(105, 30, "Congratulations!");

//Print Direction
doc.setFontStyle("normal");
doc.setFontSize(12);
doc.setTextColor(0, 0, 0);
doc.setFontStyle("normal");
doc.text(20, 82, "(Print this certificate as proof of successfully completing the course)");

//User Score
doc.setFontSize(24);
doc.setFontStyle("bold");
doc.text(20, 95, "Score:");
doc.setFontStyle("normal");
doc.text(60, 95, userScore + "%");

//Notes Heading
doc.setFontSize(24);
doc.setFontStyle("bold");
doc.text(20, 110, "Notes from course:");

//Notes Variable Information
doc.setFontSize(14);
doc.setFontStyle("normal");
doc.text(40, 120, splitNotes);

//Save PDF
doc.save('Certificate_Test.pdf');
