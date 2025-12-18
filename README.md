using System;
using System.Drawing;
using System.Windows.Forms;

namespace BalatroGame
{
    public class MainForm : Form
    {
        public MainForm()
        {
            SetupForm();
        }

        private void SetupForm()
        {
            this.Text = "Balatro";
            this.Size = new Size(900, 800); // УВЕЛИЧИЛ с 800,700
            this.StartPosition = FormStartPosition.CenterScreen;
            this.BackColor = Color.FromArgb(15, 15, 30);
            this.FormBorderStyle = FormBorderStyle.FixedSingle;
            this.MaximizeBox = false;

            // Заголовок
            Label lblTitle = new Label();
            lblTitle.Text = "BALATRO";
            lblTitle.Font = new Font("Arial", 54, FontStyle.Bold); // УВЕЛИЧИЛ шрифт
            lblTitle.ForeColor = Color.Gold;
            lblTitle.Size = new Size(500, 100);
            lblTitle.Location = new Point(200, 100);
            lblTitle.TextAlign = ContentAlignment.MiddleCenter;
            this.Controls.Add(lblTitle);

            // Версия
            Label lblVersion = new Label();
            lblVersion.Text = ".NET Edition";
            lblVersion.Font = new Font("Arial", 18, FontStyle.Italic);
            lblVersion.ForeColor = Color.LightGray;
            lblVersion.Size = new Size(300, 50);
            lblVersion.Location = new Point(300, 210);
            lblVersion.TextAlign = ContentAlignment.MiddleCenter;
            this.Controls.Add(lblVersion);

            // Кнопка "Новая игра"
            Button btnStart = new Button();
            btnStart.Text = "НОВАЯ ИГРА";
            btnStart.Font = new Font("Arial", 22, FontStyle.Bold); // УВЕЛИЧИЛ
            btnStart.Size = new Size(350, 70); // УВЕЛИЧИЛ
            btnStart.Location = new Point(275, 280);
            btnStart.BackColor = Color.FromArgb(40, 40, 60);
            btnStart.ForeColor = Color.White;
            btnStart.FlatStyle = FlatStyle.Flat;
            btnStart.Click += (sender, e) =>
            {
                GameForm gameForm = new GameForm();
                this.Hide();
                gameForm.Show();
                gameForm.FormClosed += (s, args) => this.Show();
            };
            this.Controls.Add(btnStart);

            // Кнопка "Правила игры"
            Button btnRules = new Button();
            btnRules.Text = "ПРАВИЛА ИГРЫ";
            btnRules.Font = new Font("Arial", 22, FontStyle.Bold);
            btnRules.Size = new Size(350, 70);
            btnRules.Location = new Point(275, 370);
            btnRules.BackColor = Color.FromArgb(60, 60, 90);
            btnRules.ForeColor = Color.White;
            btnRules.FlatStyle = FlatStyle.Flat;
            btnRules.Click += BtnRules_Click;
            this.Controls.Add(btnRules);

            // Кнопка "Выход"
            Button btnExit = new Button();
            btnExit.Text = "ВЫХОД";
            btnExit.Font = new Font("Arial", 22, FontStyle.Bold);
            btnExit.Size = new Size(350, 70);
            btnExit.Location = new Point(275, 460);
            btnExit.BackColor = Color.FromArgb(40, 40, 60);
            btnExit.ForeColor = Color.White;
            btnExit.FlatStyle = FlatStyle.Flat;
            btnExit.Click += (sender, e) => Application.Exit();
            this.Controls.Add(btnExit);
        }

        // Новый метод для отображения правил
        private void BtnRules_Click(object sender, EventArgs e)
        {
            // Создаем форму с правилами
            RulesForm rulesForm = new RulesForm();
            rulesForm.ShowDialog();  // ShowDialog чтобы блокировать главное меню
        }
    }
}
