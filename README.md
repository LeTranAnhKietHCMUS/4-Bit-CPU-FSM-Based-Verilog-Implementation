# 4-Bit CPU — FSM-Based Verilog Implementation

A complete 4-bit CPU design implemented in Verilog HDL, developed as a course project for
**Electronic IC Design (Thiết Kế Vi Mạch Điện Tử)**.

## Overview

This project implements a simple 4-bit CPU consisting of four key components connected
together: an Instruction Memory (ROM), a Control Unit (FSM), an Arithmetic Logic Unit (ALU),
and a set of registers. The CPU fetches and executes 16 instructions stored in ROM,
each encoded as a 13-bit data frame.

## Architecture

| Module | Description |
|--------|-------------|
| `MEM` | 16-entry instruction ROM (13-bit data frame per instruction) |
| `ALU` | 4-bit ALU supporting 16 operations |
| `ControlUnit` | 3-state FSM: Fetch → Execute → Done |
| `Reg4` | 4-bit register with synchronous load and reset |
| `system` | Top-level module wiring all components together |

## Instruction Set (16 Operations)

| OP_CODE | Operation |
|---------|-----------|
| 0000 | Pass A |
| 0001 | A + 1 |
| 0010 | A + B |
| 0011 | A + B + 1 |
| 0100 | A + (~B) + 1 (A - B) |
| 0101 | A - B + CIN |
| 0110 | A - 1 |
| 0111 | Pass A |
| 1000 | A AND B |
| 1001 | A OR B |
| 1010 | A XOR B |
| 1011 | NOT A |
| 1100 | Zero |
| 1101 | A << 1 (Shift Left) |
| 1110 | A >> 1 (Shift Right) |
| 1111 | Rotate Left A |

## Files

| File | Description |
|------|-------------|
| `CPU_final.v` | Top-level CPU design with all submodules |
| `CPU_final_tb.v` | Testbench with 16 instruction test cases |

## Simulation

The testbench runs all 16 instructions sequentially and displays expected vs. actual output
for each. Waveform is saved to `cpu_4bit_full.vcd`.

> Course: Electronic IC Design | University of Science, VNU-HCM  
> Faculty of Electronics and Telecommunications

---

# CPU 4-Bit — Thiết Kế Dựa Trên FSM bằng Verilog

Thiết kế CPU 4-bit hoàn chỉnh bằng ngôn ngữ Verilog HDL, thực hiện trong khuôn khổ môn học
**Thiết Kế Vi Mạch Điện Tử**.

## Tổng Quan

Dự án này hiện thực hóa một CPU 4-bit đơn giản gồm 4 thành phần chính: Bộ nhớ lệnh (ROM),
Khối điều khiển (FSM), Đơn vị xử lý số học và logic (ALU), và các thanh ghi.
CPU thực thi tuần tự 16 lệnh được lưu trong ROM, mỗi lệnh được mã hóa thành khung dữ liệu 13-bit.

## Kiến Trúc Hệ Thống

| Module | Mô tả |
|--------|-------|
| `MEM` | ROM lệnh 16 ô nhớ (mỗi lệnh 13-bit) |
| `ALU` | ALU 4-bit hỗ trợ 16 phép toán |
| `ControlUnit` | FSM 3 trạng thái: Fetch → Execute → Done |
| `Reg4` | Thanh ghi 4-bit có load đồng bộ và reset |
| `system` | Module cấp cao nhất kết nối toàn bộ hệ thống |

## Tập Lệnh (16 Phép Toán)

Bao gồm các phép toán số học (cộng, trừ, tăng, giảm), logic (AND, OR, XOR, NOT),
dịch bit (shift trái/phải), xoay bit và gán giá trị 0.

## Danh Sách File

| File | Mô tả |
|------|-------|
| `CPU_final.v` | Thiết kế CPU đầy đủ gồm tất cả các module con |
| `CPU_final_tb.v` | Testbench với 16 trường hợp kiểm tra |

## Mô Phỏng

Testbench chạy tuần tự toàn bộ 16 lệnh và in ra giá trị thực tế so với giá trị kỳ vọng
cho từng lệnh. Kết quả dạng sóng được lưu vào `cpu_4bit_full.vcd`.

> Môn học: Thiết Kế Vi Mạch Điện Tử  
> Trường Đại học Khoa học Tự nhiên, ĐHQG-HCM  
> Khoa Điện Tử - Viễn Thông
