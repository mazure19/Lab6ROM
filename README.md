# Lab6ROM
ROM File and Testbench

//ROM

module ROM(clock, address, out);

input [7:0] address;

input clock;

output [31:0] out;


reg [31:0] result;

assign out = result;


always @(posedge clock) begin


case (address)

8'd00: result = 32'h00450693;

8'd04: result = 32'h00100713;

8'd08: result = 32'h00b76463;

8'd12: result = 32'h00008067;

8'd16: result = 32'h006a803;

8'd20: result = 32'h00068613;

8'd24: result = 32'h00070793;

8'd28: result = 32'hffc62883;

8'd32: result = 32'h01185a63;

8'd36: result = 32'h01162023;

8'd40: result = 32'hfff78793;

8'd44: result = 32'hffc60613;

8'd48: result = 32'hfe0796e3;

8'd52: result = 32'h00279793;

8'd56: result = 32'h00f507b3;

8'd60: result = 32'h0107a023;

8'd64: result = 32'h00170713;

8'd68: result = 32'h00468693;

8'd72: result = 32'hfc1ff06f;

endcase

end


endmodule 


//Testbench

module ROM_tb();

reg [7:0] address;

wire [31:0] w;

integer idx;

integer idx0;


ROM ins(address, out);


initial


begin

	#100;
  
	$write("ROM Simulation Start\n");
	
  for(idx = 0; idx < 32; idx = idx0)

	begin
		address = idx;
    
		idx0 = idx+1;
    
		#100;
    
	end 
  
	#500;
  
end

	initial
  
	begin
  
		$monitor($time, " address = %b, out = %b", address, out);
    
	end
  
endmodule
