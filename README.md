import java.util.ArrayList;
import java.util.Collections;


public class alternative_algorithm {
	
	private int num_run;
	private int buffMem[];
	private ArrayList<Integer> frozen;
	private ArrayList<Integer> unfrozen;
	private ArrayList<Integer> run;
		
	public alternative_algorithm()
	{
		buffMem = new int [] {109, 49, 34, 68, 45, 2, 60, 38, 28, 47, 16, 19,
				34, 55, 98, 78, 76, 40, 35, 86, 10, 27, 61, 92, 99, 72, 11, 2,
				29, 16, 80, 73, 18, 12, 89, 50, 46, 36, 67, 93, 22, 14, 83, 44,
				52, 59, 10, 38, 76, 16, 24, 85 };
		
		frozen = new ArrayList<Integer>();
		unfrozen = new ArrayList<Integer>();
		run = new ArrayList<Integer>();
	}
	public void make_run(int m)
	{
		int num_run = 1;
		int num;
		
		for(num = 0; num < m; num++)
			unfrozen.add(buffMem[num]);
		
	
					
		while(num < 52)
		{
			while(frozen.size()>0)
			{
				unfrozen.add(frozen.get(0));
				frozen.remove(0);
			}
			
			while(num<52)
			{
			
				Collections.sort(unfrozen);
				
				if(unfrozen.get(0) > buffMem[num])
				{
					frozen.add(buffMem[num]);
					run.add(unfrozen.get(0));
					unfrozen.remove(0);
				}
				else
				{
					run.add(unfrozen.get(0));
					unfrozen.set(0, buffMem[num]);
				}
				
				num++;
				
				if(unfrozen.size() == 0)
				{
					show_run();				
					break;
				}
			}				
		}
		
		while(unfrozen.size()>0)
		{
			run.add(unfrozen.get(0));
			unfrozen.remove(0);
		}
		
		if(run.size() > 0) show_run();
		
		
		if(frozen.size()>0){
			while(frozen.size()>0){
				run.add(frozen.get(0));
				frozen.remove(0);			
			}
			show_run();
		}
		
		System.out.print("\n\n");
		
	}
	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		alternative_algorithm temp = new alternative_algorithm();
		temp.make_run(4);
		temp.make_run(5);
		temp.make_run(6);
		

	}
	
	
	public void show_run()
	{
		Collections.sort(run);
		System.out.print("run"+num_run++ +": ");
		while(run.size()>0)
		{
			System.out.print(run.get(0)+" ");
			run.remove(0);
		}
		System.out.print("\n");
	}

}
