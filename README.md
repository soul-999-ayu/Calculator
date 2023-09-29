# Calculator-JAVA
Calculator program written in JAVA with all basic functions.

This Calculator program is solely written by Ayush.

This calculator is purely written in java with all the basic functions like +, -, /, *,  and more. This program's UI is one of my favorites and you'll love it too. You can modify it as your need or wish.

Features of the program:
* Contains all basic functions.
* Awesome UI.
* Completed in 260 lines only.
* And many more!

Check screenshots:
![Screenshot (66)](https://user-images.githubusercontent.com/119154806/215312784-000644ab-ccf6-4ffd-ad68-fcca4b6405cf.png)
![Screenshot (68)](https://user-images.githubusercontent.com/119154806/215312789-4b8a575e-6e7c-427e-9830-706ec4780ac8.png)
![Screenshot (69)](https://user-images.githubusercontent.com/119154806/215312798-265ad985-8819-4c2f-80f6-dec6f18d36d4.png)
![Screenshot (70)](https://user-images.githubusercontent.com/119154806/215312802-1fa1306c-f025-458a-80c3-931785fd2d18.png)
![Screenshot (71)](https://user-images.githubusercontent.com/119154806/215312804-d1229de3-e428-4e22-94e9-42e2fb793156.png)

Deails about code:
* Easy to understand.
* Easy to modify.
* Very short code.

Check the code:

	import java.awt.*;
	import java.awt.event.*;
	import javax.swing.*;

	public class MyFrame extends JFrame implements ActionListener, KeyListener{

	private static final long serialVersionUID = 1L;
	
	String n1 = "",n2 = "",op = "", pa = "", k;
	JLabel disp;
	JButton num[] = new JButton[10];
	JButton butt[] = new JButton[10]; 
	
	void func() {
		if(!n2.equals("")) {
			if(op.equals("+"))
				n1 = String.valueOf(Double.parseDouble(n1) + Double.parseDouble(n2));
			if(op.equals("-"))
				n1 = String.valueOf(Double.parseDouble(n1) - Double.parseDouble(n2));
			if(op.equals("/")) {
				n1 = String.valueOf(Double.parseDouble(n1) / Double.parseDouble(n2));
				if(n2.equals("0"))
					n1 = "Undefined !";
			}
			if(op.equals("*"))
				n1 = String.valueOf(Double.parseDouble(n1) * Double.parseDouble(n2));
			if(op.equals("%")) 
				n1 = String.valueOf((Double.parseDouble(n1)/100) * Double.parseDouble(n2));
			if(!n1.equals("Undefined !")) 
				pa = n1;
			n2 = "";
			op = "";
		}
	}
	
	void remove() {
		if(op.equals("") && n1.length()>=1) {
			StringBuffer sb1 = new StringBuffer(n1);
			n1 = String.valueOf(sb1.deleteCharAt(sb1.length()-1));
		}
		else {
			if(n2.equals("") && !op.isEmpty()) {
				StringBuffer o = new StringBuffer(op);
				op ="" + o.deleteCharAt(0);
			}
			else if(n2.length()>=1){
				StringBuffer sb2 = new StringBuffer(n2);
				n2 ="" + sb2.deleteCharAt(sb2.length()-1);
			}
		}
	}
	
	void keys(char z, String n) {
		if(n.equals(n1))
			k = "n1";
		else
			k = "n2";
		switch(z) {
		case '0' : n = n + "0";
		break;
		case '1' : n = n + "1";
		break;
		case '2' : n = n + "2";
		break;
		case '3' : n = n + "3";
		break;
		case '4' : n = n + "4";
		break;
		case '5' : n = n + "5";
		break;
		case '6' : n = n + "6";
		break;
		case '7' : n = n + "7";
		break;
		case '8' : n = n + "8";
		break;
		case '9' : n = n + "9";
		break;
		}
		if(k.equals("n1")) 
			n1 = n;
		else
			n2 = n;
	}
	
	MyFrame(){
		
		//DISPLAY OF CALCULATOR
		disp = new JLabel("Calculator");
		disp.setHorizontalAlignment(JLabel.CENTER);
		disp.setOpaque(true);
		disp.setBackground(Color.RED);
		disp.setForeground(Color.black);
		disp.setFont(new Font("MV Boli", Font.PLAIN, 20));
		disp.setBounds(17, 20, 295, 50);
		disp.setVisible(true);
		
		String nam[] = {"AC", "Pre", "%", "+", "-", "*", "/", ".", "X", "="};	
		
		//BUTTON FROM 0-9
		for(int i=0; i<10; i++) {
			num[i] = new JButton(String.valueOf(i));
			num[i].setBackground(new Color(123,100,255));
			num[i].setForeground(Color.black);
			num[i].setFont(new Font("MV Boli", Font.PLAIN, 17));
			num[i].setFocusable(false);
			num[i].setVisible(true);
			num[i].addActionListener(this);
			
			butt[i] = new JButton(nam[i]);
			butt[i].setBackground(new Color(123,100,255));
			butt[i].setForeground(Color.black);
			butt[i].setFont(new Font("MV Boli", Font.PLAIN, 17));
			butt[i].setFocusable(false);
			butt[i].setVisible(true);
			butt[i].addActionListener(this); 
			
			this.add(num[i]);
			this.add(butt[i]);
		}
		
		//BUTTON POSITIONS
		butt[0].setBounds(20, 90, 65, 40);
		butt[1].setBounds(95, 90, 65, 40);
		butt[2].setBounds(170, 90, 65, 40);
		butt[3].setBounds(245, 90, 65, 40);
		
		num[1].setBounds(20, 150, 65, 40);
		num[2].setBounds(95, 150, 65, 40);
		num[3].setBounds(170, 150, 65, 40);
		butt[4].setBounds(245, 150, 65, 40);
		
		num[4].setBounds(20, 210, 65, 40);
		num[5].setBounds(95, 210, 65, 40);
		num[6].setBounds(170, 210, 65, 40);
		butt[5].setBounds(245, 210, 65, 40);
		
		num[7].setBounds(20, 270, 65, 40);
		num[8].setBounds(95, 270, 65, 40);
		num[9].setBounds(170, 270, 65, 40);
		butt[6].setBounds(245, 270, 65, 40);
		
		num[0].setBounds(20, 330, 65, 40);
		butt[7].setBounds(95, 330, 65, 40);
		butt[8].setBounds(170, 330, 65, 40);
		butt[9].setBounds(245, 330, 65, 40);
		
		//FRAME
		this.addKeyListener(this);
		this.setLocationRelativeTo(null);
		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		this.setResizable(false);
		this.setLayout(null);
		this.setSize(new Dimension(345,420));
		this.getContentPane().setBackground(Color.WHITE);
		this.add(disp);
		this.setVisible(true);
	}
	
	@Override
	public void actionPerformed(ActionEvent e) {
		if(e.getSource()==butt[0]) {
			op="";
			n1="";
			n2="";
		}
	
		for(int i=0; i<10; i++) {
			if(e.getSource()==num[i]) {
				if(n1.equals("Undefined !"))
					n1 = "";
				if(op.equals("")) 
					n1=n1 + i;
				else 
					n2=n2 + i;
		}
		}
		
		if(e.getSource()==butt[7]) {
			if(op.equals("")) {
				if(!n1.contains(".")) 
					n1=n1 + ".";
			}
			else {
				if(!n2.contains(".")) 
					n2=n2 + ".";
				}
		}
		
		if(e.getSource()==butt[8]) 
			remove();
		
		if(!n1.isEmpty()) {
			if(e.getSource()==butt[3]) 
				op = "+";
			if(e.getSource()==butt[4]) 
				op = "-";
			if(e.getSource()==butt[5]) 
				op = "*";
			if(e.getSource()==butt[6]) 
				op = "/";
			if(e.getSource()==butt[2]) 
				op = "%";
		}
		
		if(e.getSource()==butt[9]) 
			func();
		
		if(e.getSource()==butt[1]) {
			n1 = pa;
			op="";
			n2="";
		}
		
		disp.setText(n1 + " " + op + " " + n2);
	}
	
	@Override
	public void keyTyped(KeyEvent y) {}
	
	@Override
	public void keyPressed(KeyEvent y) {
		if(y.getKeyCode()==KeyEvent.VK_BACK_SPACE || y.getKeyCode()==KeyEvent.VK_DELETE )
			remove();
	}
	
	@Override
	public void keyReleased(KeyEvent y) {
		char x = y.getKeyChar();
		if(n1.equals("Undefined !"))
			n1 = "";
		
		if(!n1.isEmpty()) {
			switch(y.getKeyChar()) {
				case '+' : op = "+";
				break;
				case '-' : op = "-";
				break;
				case '*' : op = "*";
				break;
				case '/' : op = "/";
				break;
				case '%' : op = "%";
				break;
				case '=' : func();
				break;
			}
		}
		
		if(y.getKeyCode()==KeyEvent.VK_ENTER) 
			func();
		
		if(op.equals("")) 
			keys(x, n1);
		else 
			keys(x, n2);

	disp.setText(n1 + " " + op + " " + n2);
	}
	}

Issues:
* I did not find any issue but there may be some.

Conclusion:
You can download the JAR and exe file from release section. you can use this code as long as you don't consider it as your own work.
