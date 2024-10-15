# ChemoCraft-ACM-Research-2024

#### **Step 1: Install Conda (Anaconda or Miniconda)**

##### **macOS**
1. Download and install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) (lighter) or [Anaconda](https://www.anaconda.com/products/distribution) (includes more libraries).
2. Open a terminal and verify the installation:
   
   ```bash
   conda --version
   ```

##### **Windows**
1. Download and install [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or [Anaconda](https://www.anaconda.com/products/distribution).
2. Open **Anaconda Prompt** and verify the installation:
   
   ```bash
   conda --version
   ```

#### **Step 2: Create and Activate a Virtual Environment**

##### **macOS & Windows**
1. Create a virtual environment using Conda:
   
   ```bash
   conda create --name myenv python=3.x
   ```
   Replace `myenv` with your environment name and `3.x` with the desired Python version.
3. Activate the virtual environment:
   
   ```bash
   conda activate myenv
   ```

#### **Step 3: Install Jupyter Notebook**

1. Install Jupyter Notebook in your Conda environment:
   
   ```bash
   conda install jupyter
   ```
3. Launch Jupyter Notebook:
   
   ```bash
   jupyter notebook
   ```

#### **Step 4: Install Git and Clone the Repository**

##### **macOS**
1. Install Git using Homebrew (if not installed):
   
   ```bash
   brew install git
   ```
3. Clone the repository:
   
   ```bash
   git clone https://github.com/vaipos/ChemoCraft-ACM-Research-2024.git
   ```

##### **Windows**
1. Download and install Git from [Git's official site](https://git-scm.com/).
2. Clone the repository using Git Bash or Anaconda Prompt:
   
   ```bash
   git clone https://github.com/vaipos/ChemoCraft-ACM-Research-2024.git
   ```

#### **Step 5: Set Up Jupyter Notebook with GitHub Integration**

1. Navigate to the project directory (replace `your-repo`):
   
   ```bash
   cd your-repo
   ```
3. Open Jupyter Notebook:
   
   ```bash
   jupyter notebook
   ```

4. To sync your Jupyter notebooks with GitHub:
   - After making changes in your notebooks, save the notebook and close it.
   - Run the following Git commands to track and push your changes:
     
     ```bash
     git add .
     git commit -m "Update notebook"
     git push origin main
     ```

---
