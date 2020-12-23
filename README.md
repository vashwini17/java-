# java-
import java.io.File;
import java.io.FileReader;
import java.io.BufferedReader;
import java.util.*;


public class AuditLargeScale{
    public static void main(String[] args) throws Exception {


        File F2 = new File("C:\\Users\\vashw\\Documents\\b.txt");
        BufferedReader br1 = new BufferedReader(new FileReader(F2));

        Hashtable<String, String> dt2 = new Hashtable<String, String>();

        for (String line1 = br1.readLine(); line1 != null; line1 = br1.readLine()) {

            String[] str1 = line1.split("\\s+");

            dt2.put(str1[0],str1[1]);

        }
        br1.close();

        File F1 = new File("C:\\Users\\vashw\\Documents\\a.txt");
        BufferedReader br = new BufferedReader(new FileReader(F1));



        for (String line = br.readLine(); line != null; line = br.readLine()) {
            String[] str = line.split("\\s+");

            if (dt2.get(str[0]) == null) {
                System.out.println(str[0] + " Found in A not in B");
            } else if (dt2.get(str[0]) != null) {

                if (!str[1].equals(dt2.get(str[0]))) {
                    System.out.println(str[0] + " Does not Match Values are " + str[1] +" " + dt2.get(str[0]));
                }


            }
            dt2.remove(str[0]);
        }

        br.close();


        Enumeration enu = dt2.keys();
        while (enu.hasMoreElements()) {
            System.out.println(enu.nextElement() + " Found in B not in A");
        }

    }
}
