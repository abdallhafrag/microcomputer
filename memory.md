module memory(input clk,R_wn,
              input [7:0] address,
              inout[15:0]  data_Bus);
              reg[15:0] Temp_data;
           
reg [15:0] MEM [255:0]; //256memory loation *16-bit lenght addressed by 8-bit address        
        initial begin
    
$readmemh("D:/farrag/MEM.txt", MEM); //read memmory         end
        end
        always @(posedge clk) begin
          if (!R_wn) 
          begin 
          MEM[address] = data_Bus; 
        end
        else
        begin 
        Temp_data= MEM[address];
        end
    end            
        assign data_Bus= R_wn ? Temp_data:'hzzzz;
    
        
      endmodule
