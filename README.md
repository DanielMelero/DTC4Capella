# 🧩 Dataflow Tabular Chart Exporter for Capella

## Overview

This tool automatically generates **Dataflow Tabular Charts (DTC)** from **Capella** models.
It allows system engineers to visualize how data moves through a system — layer by layer — directly from a **Functional Chain** in Capella.

The tool extends the open-source **Dataflow Tabular Chart** developed by [Yves Rütschlé](https://github.com/yrutschle/dtc) and integrates it into **Capella 7.0** using the **Python4Capella** add-on.

---

## Motivation

Traditional architecture diagrams focus mainly on **network topology** — what connects to what.
But they often hide **how protocols stack up** and **where security boundaries** are actually crossed.

The **Dataflow Tabular Chart** solves this by showing each dataflow vertically, through its protocol layers (Ethernet, IP, TCP, SMTP, etc.), across the systems and functions involved.

By integrating this with Capella:

* System engineers can **generate DTC diagrams automatically** from existing models.
* The diagrams stay **consistent with the model**, no manual redrawing needed.
* They provide **clear, security-relevant visualizations** for architecture reviews.

---

## Examples

### ✉️ Example 1 – E-mail in DMZ

An e-mail server is placed in a **Demilitarized Zone (DMZ)** behind two firewalls.
The Dataflow Tabular Chart shows that the actual **message content** still travels through to the internal e-mail client — crossing multiple boundaries and exposing a potential attack path.

### 💻 Example 2 – E-mail Client in DMZ

In this variation, the e-mail client is also moved into the DMZ and accessed via a remote desktop session.
The Dataflow Tabular Chart now clearly shows that **only the human-readable content** reaches the internal network — significantly reducing exposure.

These two cases demonstrate how DTCs make **security barriers and data exposure** visible in a way that top-down diagrams often miss.

---

## User Guide

### Requirements

* **Capella 7.0**
* **Python4Capella add-on** installed

### Usage

1. Open your Capella model.
2. In the **Project Explorer**, **right-click** on a **Functional Chain**.
3. Select **“Export Dataflow Tabular Chart”**.
4. The script will:

   * Extract all data exchanges from the selected Functional Chain.
   * Produce a `.svg` diagram

The generated diagram will appear in the same directory as your model, with the same name as the selected Functional Chain.
