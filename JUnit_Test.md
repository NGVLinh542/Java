# Thêm Xoá Sửa
Dưới đây là một ví dụ về cách tạo đối tượng SinhVien và danh sách đối tượng SinhVien trong Java:

```java

import java.util.ArrayList;

import java.util.List;

public class SinhVien {

    private String ten;

    private int tuoi;

    public SinhVien(String ten, int tuoi) {

        this.ten = ten;

        this.tuoi = tuoi;

    }

    public String getTen() {

        return ten;

    }

    public void setTen(String ten) {

        this.ten = ten;

    }

    public int getTuoi() {

        return tuoi;

    }

    public void setTuoi(int tuoi) {

        this.tuoi = tuoi;

    }

}

public class DanhSachSinhVien {

    private List<SinhVien> danhSach;

    public DanhSachSinhVien() {

        danhSach = new ArrayList<>();

    }

    public void them(SinhVien sv) {

        danhSach.add(sv);

    }

    public void sua(SinhVien cu, SinhVien moi) {

        int index = danhSach.indexOf(cu);

        if (index != -1) {

            danhSach.set(index, moi);

        }

    }

    public void xoa(SinhVien sv) {

        danhSach.remove(sv);

    }

}

```

Bạn có thể tạo một JUnit test để kiểm tra các phương thức thêm, sửa và xoá trong lớp DanhSachSinhVien. Bạn có muốn biết thêm chi tiết về cách viết JUnit test không?

Có.


Dưới đây là một ví dụ về cách viết JUnit test để kiểm tra các phương thức thêm, sửa và xoá trong lớp DanhSachSinhVien:

```java

import org.junit.Test;

import static org.junit.Assert.*;

public class DanhSachSinhVienTest {

    @Test

    public void testThem() {

        DanhSachSinhVien ds = new DanhSachSinhVien();

        SinhVien sv = new SinhVien("Nguyen Van A", 20);

        ds.them(sv);

        assertEquals(1, ds.danhSach.size());

        assertEquals(sv, ds.danhSach.get(0));

    }

    @Test

    public void testSua() {

        DanhSachSinhVien ds = new DanhSachSinhVien();

        SinhVien sv1 = new SinhVien("Nguyen Van A", 20);

        ds.them(sv1);

        SinhVien sv2 = new SinhVien("Nguyen Van B", 21);

        ds.sua(sv1, sv2);

        assertEquals(1, ds.danhSach.size());

        assertEquals(sv2, ds.danhSach.get(0));

    }

    @Test

    public void testXoa() {

        DanhSachSinhVien ds = new DanhSachSinhVien();

        SinhVien sv = new SinhVien("Nguyen Van A", 20);

        ds.them(sv);

        ds.xoa(sv);

        assertTrue(ds.danhSach.isEmpty());

    }

}

```

Bạn có thể chạy các test trên bằng cách sử dụng JUnit. Bạn có muốn biết thêm chi tiết về cách cài đặt và sử dụng JUnit không?

# Nhập Xuất File
Dưới đây là một ví dụ về cách tạo đối tượng SinhVien và danh sách đối tượng SinhVien, nhập và xuất file, và tạo JUnit Test kiểm tra nhập và xuất file trong Java:

```java

import java.io.*;

import java.util.*;

class SinhVien {

    private String ten;

    private int tuoi;

    public SinhVien(String ten, int tuoi) {

        this.ten = ten;

        this.tuoi = tuoi;

    }

    public String getTen() {

        return ten;

    }

    public void setTen(String ten) {

        this.ten = ten;

    }

    public int getTuoi() {

        return tuoi;

    }

    public void setTuoi(int tuoi) {

        this.tuoi = tuoi;

    }

}

public class SinhVienTest {

    public static void main(String[] args) {

        // Tạo danh sách đối tượng SinhVien

        ArrayList<SinhVien> sinhViens = new ArrayList<>();

        sinhViens.add(new SinhVien("Nguyen Van A", 20));

        sinhViens.add(new SinhVien("Tran Thi B", 21));

        // Xuất danh sách đối tượng SinhVien ra file

        try (FileWriter writer = new FileWriter("sinhvien.txt")) {

            for (SinhVien sinhVien : sinhViens) {

                writer.write(sinhVien.getTen() + "," + sinhVien.getTuoi() + "\n");

            }

        } catch (IOException e) {

            e.printStackTrace();

        }

        // Nhập danh sách đối tượng SinhVien từ file

        ArrayList<SinhVien> sinhViensFromFile = new ArrayList<>();

        try (BufferedReader reader = new BufferedReader(new FileReader("sinhvien.txt"))) {

            String line;

            while ((line = reader.readLine()) != null) {

                String[] parts = line.split(",");

                String ten = parts[0];

                int tuoi = Integer.parseInt(parts[1]);

                sinhViensFromFile.add(new SinhVien(ten, tuoi));

            }

        } catch (IOException e) {

            e.printStackTrace();

        }

        // In ra danh sách đối tượng SinhVien từ file

        for (SinhVien sinhVien : sinhViensFromFile) {

            System.out.println(sinhVien.getTen() + " - " + sinhVien.getTuoi());

        }

    }

}

```

```java

import org.junit.Test;

import static org.junit.Assert.*;

public class SinhVienTestTest {

    @Test

    public void testNhapXuatFile() {

        // Tạo danh sách đối tượng SinhVien

        ArrayList<SinhVien> sinhViens = new ArrayList<>();

        sinhViens.add(new SinhVien("Nguyen Van A", 20));

        sinhViens.add(new SinhVien("Tran Thi B", 21));

        // Xuất danh sách đối tượng SinhVien ra file

        try (FileWriter writer = new FileWriter("sinhvien.txt")) {

            for (SinhVien sinhVien : sinhViens) {

                writer.write(sinhVien.getTen() + "," + sinhVien.getTuoi() + "\n");

            }

        } catch (IOException e) {

            e.printStackTrace();

        }

        // Nhập danh sách đối tượng SinhVien từ file

        ArrayList<SinhVien> sinhViensFromFile = new ArrayList<>();

        try (BufferedReader reader = new BufferedReader(new FileReader("sinhvien.txt"))) {

            String line;

            while ((line = reader.readLine()) != null) {

                String[] parts = line.split(",");

                String ten = parts[0];

                int tuoi = Integer.parseInt(parts[1]);

                sinhViensFromFile.add(new SinhVien(ten, tuoi));

            }

        } catch (IOException e) {

            e.printStackTrace();

        }

        // Kiểm tra xem danh sách đối tượng SinhVien từ file có giống với danh sách ban đầu hay không

        assertEquals(sinhViens.size(), sinhViensFromFile.size());

        for (int i = 0; i < sinhViens.size(); i++) {

            assertEquals(sinhViens.get(i).getTen(), sinhViensFromFile.get(i).getTen());

            assertEquals(sinhViens.get(i).getTuoi(), sinhViensFromFile.get(i).getTuoi());

        }

    }

}

```

Hy vọng ví dụ trên sẽ gi
