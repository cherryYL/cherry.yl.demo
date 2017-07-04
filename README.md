# cherry.yl.demo
package me.ele.zs;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;

public class MapTest {
	
	public static void main(String[] args) {
		setUp();
		testMapLoopA();
		testMapLoopB();
	}
	private static Map<Integer, String> infos = new HashMap<Integer, String>();  
    
    public static void setUp() {  
        for (int i=0; i<10000000; i++) {  
            infos.put(i, "test information" + i);  
        }  
        System.out.println("setUp is done.");  
    }  
    
    private static void testMapLoopA() {  
        Iterator<Map.Entry<Integer, String>> iterator = infos.entrySet().iterator();  
        long startTime = System.currentTimeMillis();  
        while (iterator.hasNext()) {  
            Map.Entry<Integer, String> entry = iterator.next();  
            int key = entry.getKey();  
            String val = entry.getValue();  
        }  
          
        System.out.println("A solution takes in looping Map with 1000000 entries:"  
                    + (System.currentTimeMillis()-startTime) + " milli seconds");  
    }  
    
    private static void testMapLoopB() {  
        Iterator<Integer> iterator = infos.keySet().iterator();  
        long startTime = System.currentTimeMillis();  
        while (iterator.hasNext()) {              
            int key = iterator.next();  
            String val = infos.get(key);  
        }  
          
        System.out.println("B solution takes in looping Map with 1000000 entries:" +  
                   (System.currentTimeMillis()-startTime) + " milli seconds");  
    } 

}
