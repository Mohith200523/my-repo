# my-repo﻿using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Data.Common;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace CrimeRecord
{
    public partial class AccusedRecord : Form
    {
        public AccusedRecord()
        {
            InitializeComponent();
        }

        public void dataload()
        {
            String Sql = "Select * from Table_Accused";
            accusedgridview.DataSource = DBConnection.GetTableByQuery(Sql);
        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void btnview_Click(object sender, EventArgs e)
        {
            dataload();
        }

        private void pictureBox2_Click(object sender, EventArgs e)
        {

        }

        private void btnexit_Click(object sender, EventArgs e)
        {
            this.Hide();
            SecondDashBoard sd = new SecondDashBoard();
            sd.ShowDialog();
        }

        private void bunifuFlatButton1_Click(object sender, EventArgs e)
        {
            this.WindowState = FormWindowState.Minimized;
        }

        private void bunifuFlatButton2_Click(object sender, EventArgs e)
        {
            this.Hide();
            SecondDashBoard sd = new SecondDashBoard();
            sd.ShowDialog();
        }

        private void bunifuGradientPanel7_Paint(object sender, PaintEventArgs e)
        {

        }

        private void accusedgridview_CellContentClick(object sender, DataGridViewCellEventArgs e)
        {
            //get
            String aid = accusedgridview.Rows[e.RowIndex].Cells[0].Value.ToString();
            String fullname = accusedgridview.Rows[e.RowIndex].Cells[1].Value.ToString();
            String fathername = accusedgridview.Rows[e.RowIndex].Cells[2].Value.ToString();
            String address = accusedgridview.Rows[e.RowIndex].Cells[3].Value.ToString();
            String nic = accusedgridview.Rows[e.RowIndex].Cells[4].Value.ToString();
            String gender = accusedgridview.Rows[e.RowIndex].Cells[5].Value.ToString();
            String status = accusedgridview.Rows[e.RowIndex].Cells[6].Value.ToString();
            String cont = accusedgridview.Rows[e.RowIndex].Cells[6].Value.ToString();
            String email = accusedgridview.Rows[e.RowIndex].Cells[6].Value.ToString();
            String photo = accusedgridview.Rows[e.RowIndex].Cells[6].Value.ToString();
            String fingerprint = accusedgridview.Rows[e.RowIndex].Cells[6].Value.ToString();
            //set
            txtaccusedid.Text = aid;
            txtfullname.Text = fullname;
            txtfathername.Text = fathername;
            txtaddress.Text = address;
            txtnic.Text = nic;
            txtgender.Text = gender;
            txtstatus.Text = status;
            txtcontact.Text = cont;
            txtemail.Text = email;
            txtphoto.Text = photo;
            txtfingerprint.Text = fingerprint;
            btnsave.Enabled = false;
            btnview.Enabled = false;
        }

        private void btndelete_Click(object sender, EventArgs e)
        {
            string query = "Delete from Table_Accused where Accused_ID = '" + txtaccusedid.Text + "'";
            accusedgridview.DataSource = DBConnection.GetTableByQuery(query);
            MessageBox.Show("Accused Deleted Successfully");
            dataload();
        }

        private void btnnew_Click(object sender, EventArgs e)
        {
            btnsave.Enabled = true;
            txtfullname.Text = "";
            txtaddress.Text = "";
            txtcontact.Text = "";
            txtemail.Text = "";
            txtgender.Text = "";
            txtnic.Text = "";
            txtstatus.Text = "";
            txtphoto.Text = "";
            txtfingerprint.Text = "";
            dataload();
        }

        private void btnsave_Click(object sender, EventArgs e)
        {
            String Sql = "Insert into Table_Accused(Accused_fullname, Section_of_Law, Complain_Status, Complain_Details, Victim_Name, Accused_Name) " +
                "values('" + txtfullname.Text + "', '" + txtfathername.Text + "', '" + txtaddress.Text + "', '" + txtnic.Text + "', '" + txtgender.Text + "', '" + txtstatus.Text + "', '" + txtcontact.Text + "', '" + txtemail.Text + "')".ToString();
            accusedgridview.DataSource = DBConnection.GetTableByQuery(Sql);
            dataload();
        }

        private void btnupdate_Click(object sender, EventArgs e)
        {
            String query = "update Table_Accused set fullname='" + txtfullname.Text + "',Section_of_Law='" + txtfathername.Text + "',Complain_Status='" + txtaddress.Text + "',Complain_Details='" + txtnic.Text + "',Victim_Name='" + txtgender.Text + "',Accused_Name='" + txtstatus.Text + "' where Accused_ID='" + txtaccusedid.Text + "' ";
            accusedgridview.DataSource = DBConnection.GetTableByQuery(query);
            MessageBox.Show("Data Updated Successfully");
            dataload();
            btnsave.Enabled = true;
        }
    }
}
