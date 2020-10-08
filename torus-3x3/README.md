#########################################################################################
3x3 Torus Architecture with 1 main memory

L1 = 8 L1 cache for 8 core x86 processors
L2 = L2 cache for 8 core x86 processors
MM = One main memory for 8 core processor
 ____   ____       ____   ____   ____   ____       ____  
| L1 | | L1 | ... | L1 | | L1 | | L1 | | L1 | ... | L1 |   
|____| |____|     |____| |____| |____| |____|     |____|

   -------------------------------------------------------
  |                                                       |
  |    		Local Interconnect Network
  |							  |
   -------------------------------------------------------
          ____   ____   ____   ____   ____   ____   
         | L2 | | L2 | | L2 | | L2 | | L2 | | L2 |
         |____| |____| |____| |____| |____| |____|


   -------------------------------------------------------
  |                                                       |
  |   		   3x3 Torus Interconnect   
  |							  |
   -------------------------------------------------------

		  	  ____   
			 | MM |
			 |____|


########################################################################################

System simulation

test-threads program
m2s --x86-sim detailed --x86-config x86-config.ini --ctx-config ctx-config.ini --mem-config mem-config.ini --net-config net-config.ini --x86-report x86-report-ts-case0.rep

test-args program
m2s --x86-sim detailed --x86-config x86-config.ini --ctx-config ctx-config-testargs.ini --mem-config mem-config.ini --net-config net-config.ini --x86-report x86-report-ts-case0.rep

test-sort program
m2s --x86-sim detailed --x86-config x86-config.ini --ctx-config ctx-config-testsorts.ini --mem-config mem-config.ini --net-config net-config.ini --x86-report x86-report-ts-case0.rep

########################################################################################

Network simulation:
To Run simulation, type (or copy):

$>m2s --net-sim mynet --net-config net-config.ini --net-msg-size 72 --net-max-cycles 1000  --net-injection-rate 20 --net-report net-sim.rep --net-visual net.vis 

----------------------------------------------------------------------------------------
%% This simulation runs for 1000 cycle. In this period, at each cycle, 8 nodes inject mesh architecture a message of size 72 in the network. 
%% Network report is returned in the file net.rep 
----------------------------------------------------------------------------------------

In order to produce the visualization graph of this network in eps format, run the 
python script graphplot, which resides in folder samples/network/.

$> ./samples/network/graphplot net.vis net.eps


----------------------------------------------------------------------------------------
%% Cores = 8	Total Multicore processor 
%%Threads = 1 	Total Hardware Threads
%%Frequency = 1000
%%Processing nodes = Cores x Threads = 8 x 1 = 8
----------------------------------------------------------------------------------------
