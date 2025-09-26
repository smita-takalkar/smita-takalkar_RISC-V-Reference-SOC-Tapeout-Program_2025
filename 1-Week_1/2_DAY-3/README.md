# DAY 3: Combinational and Sequential Optimizations

## 1. Introduction to Optimizations

### SKY130RTL D3SK1 L1 – Introduction to Optimizations Part 1

* **Combinational logic optimization**: The process of squeezing logic to achieve an optimized design in terms of **area** and **power**.
* **Techniques for combinational optimization**:

  * **Constant propagation**: A direct optimization technique where constant values are propagated to simplify logic.
    ![const_propogationex](https://github.com/user-attachments/assets/457b7e5e-e2f6-495c-b620-f8f524e540ea)

  * **Boolean logic optimization**: Using methods like **K-map** and **Quine–McCluskey** for simplification.

### SKY130RTL D3SK1 L2 – Introduction to Optimizations Part 2

* **Sequential logic optimization**:

  * **Basic techniques**: Sequential constant propagation.
  * **Advanced techniques**:

    * State optimization
    * Retiming
    * Sequential logic cloning (floorplan-aware synthesis)

### SKY130RTL D3SK1 L3 – Introduction to Optimizations Part 3

* Consolidates both **combinational** and **sequential** optimization concepts.

---

## 2. Combinational Logic Optimizations

<img width="1600" height="900" alt="opt_check" src="https://github.com/user-attachments/assets/16d4be40-f4db-4859-a7f8-3ed2af1bfa3f" />
<img width="1600" height="900" alt="opt_check2" src="https://github.com/user-attachments/assets/f1452631-f627-459b-8549-84c2db5eea8d" />
<img width="1600" height="900" alt="opt_check3" src="https://github.com/user-attachments/assets/bf9c979f-45b5-48ac-be12-515d82fa5721" />
<img width="1600" height="900" alt="opt_check4" src="https://github.com/user-attachments/assets/f2b6198b-8fbc-4cb1-814f-d91c10d7b8da" />



---

## 3. Sequential Logic Optimizations
<img width="1600" height="900" alt="dff_const1_yosys" src="https://github.com/user-attachments/assets/ab2c7ecf-a638-4ca3-9bc9-bc8ca52897f4" />
<img width="1600" height="900" alt="dff_const2_yosys" src="https://github.com/user-attachments/assets/f5b8cf71-5f8f-44a0-bdc2-6f305e5bc6d8" />
<img width="1600" height="900" alt="dff_const3_yosys" src="https://github.com/user-attachments/assets/4398b31e-3faa-4ae1-acaa-35c2d7b1e4f1" />
<img width="1600" height="900" alt="dff_const4_yosys" src="https://github.com/user-attachments/assets/5a308dc8-3443-47a6-9e95-bc8668893b90" />
<img width="1600" height="900" alt="multiple_module_opt" src="https://github.com/user-attachments/assets/eb9ecc08-5ab1-4b47-9ab4-0e6b8b090539" />
<img width="1600" height="900" alt="multiple_module_opt2" src="https://github.com/user-attachments/assets/e0948d1c-86a5-418b-ba57-88e232e94622" />


---

## 4. Sequential Optimizations for Unused Outputs
<img width="1600" height="900" alt="counter_opt_unused_output_opti" src="https://github.com/user-attachments/assets/be182b1d-93ae-426d-bfa3-8abdd1aa2df2" />
<img width="1600" height="900" alt="counter_opt2_aftermodification" src="https://github.com/user-attachments/assets/486c1ade-dbe1-4fe0-8c83-01f183ec7ce0" />


Focuses on optimizing designs by removing or simplifying **unused sequential outputs**, thereby reducing unnecessary resource usage in the synthesized design.

---



