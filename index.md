---
layout: default
title: Home
permalink: /
---
  

## About Me
<a id="about"></a>

I am a second-year student at the University of Kajaani, studying AI and data engineering. I am passionate about data and machine learning methods. Currently working on a project that involves data processing and machine learning.

## Education

- Kajaani University of Applied Sciences  
Information and Communication Technology   
From Data to Artificial Intelligence  
2023 - present

- Mänttä Region Education Center  
Vocational Education in Information and Communication Technology  
IT Support Specialist  
2021 – 2023

## Projects
<a id="projects"></a>

Here are some of the projects I've worked on, available via the links below. Some projects are private and available upon request. In my GitHub repository you can find more public projects.

<!-- Data Processing -->
<figure>
  <button id="toggle-data-processing" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/data_proces.svg" alt="Data Processing Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Data Processing</span>
  </button>
  <div id="data-processing-container" style="display: none; margin-top: 20px;">
    <p>
    <h2>Data Management in Indoor Positioning</h2>
      <p>
        This project focused on developing a system infrastructure for collecting, processing, and analyzing indoor positioning data. The key goal was to enable efficient handling of historical location data and visualize it for decision-making purposes.
      </p>

      <h2>Key Accomplishments</h2>
      <ul>
        <li>Data preprocessing using <strong>Pandas</strong>, <strong>DuckDB</strong>, and SQL for filtering, aggregating, and joining datasets.</li>
        <li>Visualization of data using <strong>Seaborn</strong>, <strong>Matplotlib</strong>, and custom Python scripts to create heatmaps, scatterplots, and trend graphs.</li>
        <li>Developed analytical models to:
          <ul>
            <li>Correlate weather data (retrieved from the Finnish Meteorological Institute) with customer visits.</li>
            <li>Monitor checkout utilization and identify inefficiencies in queue management.</li>
            <li>Analyze customer paths and optimize store layouts using cart speed and distance metrics.</li>
          </ul>
        </li>
        <li>Implemented a basic predictive model using <strong>Random Forest</strong> to estimate customer visits based on weather and campaign data.</li>
      </ul>

      <h2>Tools and Technologies</h2>
      <p>
        The project utilized the following tools and technologies to manage tasks and ensure efficiency:
      </p>
      <ul>
        <li><strong>GitLab</strong> for version control and project management (milestones, issue boards).</li>
        <li><strong>Streamlit</strong> for creating an interactive dashboard to present insights.</li>
        <li><strong>Jupyter Notebook</strong> for data analysis and model development.</li>
        <li><strong>Clockify</strong> for time tracking and workload analysis.</li>
        <li><strong>Python</strong> with libraries like Pandas, Seaborn, and Scikit-learn for data processing and machine learning.</li>
      </ul>

      <h2>Challenges and Solutions</h2>
      <p>
        Handling large datasets posed memory and performance challenges. These were mitigated by optimizing data queries, using efficient algorithms, and reducing data density.
        Additionally, iterative development under the <strong>Scrum framework</strong> helped adapt to evolving requirements and address bottlenecks effectively.
      </p>

      <h2>Outcome</h2>
      <p>
        The project successfully demonstrated the ability to manage large-scale data processing, create actionable insights through visualizations, and prototype predictive models. The interactive dashboard provided a valuable tool for analyzing customer behavior and optimizing store operations.
      </p>
      <p>This project is privately hosted on GitLab and available upon request.</p>
    </p>
  </div>
</figure>

<!-- Data Pipeline -->
<figure>
  <button id="toggle-data-pipeline" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/data_pipe.svg" alt="Data Pipeline Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Data Pipeline</span>
  </button>
  <div id="data-pipeline-container" style="display: none; margin-top: 20px;">
    <p>
    <h2>Objective</h2>
    <p>The project aims to create a data pipeline using the Digitraffic API to fetch train data. The data is stored in a staging folder, then processed through bronze, silver, and gold stages. The final output is visualized using Evidence. The project also uses dbt for database documentation and data modeling, all visualized within a Docker environment.</p>

    <h2>Architecture</h2>
    <p>The database uses DuckDB as a data warehouse. SQL-based dbt models retrieve desired information, with each data model building upon the previous layer.</p>

    <h2>Pipeline</h2>
    <p>The pipeline processes train data for specific trains (7, 8, 10) over a specified time period (01.10.2024 - 03.11.2024). This can be adjusted as needed. Data is fetched using Digitraffic API and staged for processing.</p>

    <h2>Data Processing Stages</h2>
    <ul>
        <li><strong>Bronze:</strong> Initial raw data with data types and surrogate keys defined.</li>
        <li><strong>Silver:</strong> Intermediate tables with detailed stop, train, and delay information.</li>
        <li><strong>Gold:</strong> Finalized tables for visualization, focusing on delays.</li>
    </ul>

    <h2>Visualization</h2>
    <p>Weekly delays are visualized with bar and line charts. Bar charts show average delays in minutes, while line charts illustrate train-specific delays weekly.</p>

    <h2>Future Development</h2>
    <p>Automate the pipeline to prompt users for time periods and trains, simplifying usage for non-technical users. The ultimate goal is full automation up to the Evidence visualization step.</p>

    <h2>Links</h2>
    <ul>
        <li><a href="https://github.com/Carmantis/VR-Datapipeline">GitHub Repository</a></li>
        <li><a href="https://www.digitraffic.fi/rautatieliikenne/">Digitraffic</a></li>
        <li><a href="https://docs.evidence.dev/">Evidence</a></li>
        <li><a href="https://www.getdbt.com/">dbt</a></li>
    </ul>
    </p>
  </div>
</figure>

<!-- Machine Learning -->
<figure>
  <button id="toggle-machine-learning" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/ai.svg" alt="Machine Learning Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Machine Learning</span>
  </button>
  <div id="machine-learning-container" style="display: none; margin-top: 20px;">

    <h2>Introduction</h2>
    <p>
        This project integrates modern data engineering practices and machine learning 
        to forecast quarterly metrics using a Long Short-Term Memory (LSTM) model.
        We employed <strong>dbt</strong>, <strong>DuckDB</strong>, and 
        <strong>Streamlit</strong> to create a robust data pipeline, following the 
        <em>Medallion Architecture</em> (Bronze, Silver, and Gold layers). This all work in Docker containers.
        Key tasks included data ingestion, feature engineering, model training, and 
        interactive dashboard visualization.
    </p>

    <!-- Architecture -->
    <h2>Architecture: The Medallion Approach</h2>
    <p>
        The data flow is structured into three main layers to ensure scalability, 
        clarity, and reliability:
    </p>
    <ul>
        <li><strong>Bronze Layer:</strong> Raw data (from CSVs) is 
        loaded into DuckDB without transformations.</li>
        <li><strong>Silver Layer:</strong> Data is cleaned, validated, and normalized. 
        Missing values are addressed with <code>KNN-Imputer</code>, and features are 
        standardized with <code>MinMaxScaler</code>.</li>
        <li><strong>Gold Layer:</strong> Aggregated and enriched data is finalized 
        for machine learning tasks and analytical queries. Prediction outputs are 
        also stored here.</li>
    </ul>

    <!-- ETL Process -->
    <h2>ETL Process</h2>
    <p>
        The data transformation workflow (powered by <strong>dbt</strong>) is divided 
        into the following phases:
    </p>
    <ol>
        <li><strong>Extract:</strong> Data is pulled from source files into 
        the Bronze layer.</li>
        <li><strong>Transform:</strong> The Silver layer processes data for missing 
        values, anomalies, and feature scaling. Additionally, features like unit 
        type or quarter identifiers are one-hot encoded.</li>
        <li><strong>Load:</strong> The final Gold layer stores curated data and 
        houses predicted values. These predictions are then accessed and visualized 
        in <strong>Streamlit</strong>.</li>
    </ol>

    <!-- Key Highlights -->
    <h2>Key Highlights</h2>
    <ul>
        <li><strong>LSTM Model Development:</strong> A TensorFlow/Keras-based model 
        trained on historical data to forecast future metrics.</li>
        <li><strong>Data Quality Management:</strong> Missing data handled using 
        <code>KNN-Imputer</code> and anomalous values corrected during transformations.</li>
        <li><strong>Feature Engineering:</strong> One-hot encoding of categorical 
        variables (units, quarters) and scaling with <code>MinMaxScaler</code>.</li>
        <li><strong>Model Evaluation:</strong> Metrics such as MAE, RMSE, and R² 
        were used to gauge performance.</li>
        <li><strong>Streamlit Dashboard:</strong> Interactive interface to compare 
        historical vs. predicted values with dynamic filtering and various 
        visualizations (line, scatter, bar charts).</li>
    </ul>

    <!-- Results -->
    <h2>Results</h2>
    <p>
        By incorporating a structured pipeline with dbt and DuckDB, we achieved 
        consistent data transformations and a reliable environment for 
        machine learning. The LSTM model demonstrated a strong capability to 
        predict quarterly metrics, and the Streamlit application offered 
        a user-friendly platform for exploring both historical and forecasted data.
    </p>
    <p>This project is privately hosted on GitHub and available upon request.</p>
  </div>
</figure>

<script>
  // Data Processing toggle
  document.getElementById("toggle-data-processing").addEventListener("click", function() {
    const container = document.getElementById("data-processing-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Data Processing";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Data Processing";
      logo.style.transform = "rotate(0deg)";
    }
  });

  // Data Pipeline toggle
  document.getElementById("toggle-data-pipeline").addEventListener("click", function() {
    const container = document.getElementById("data-pipeline-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Data Pipeline";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Data Pipeline";
      logo.style.transform = "rotate(0deg)";
    }
  });

  // Machine Learning toggle
  document.getElementById("toggle-machine-learning").addEventListener("click", function() {
    const container = document.getElementById("machine-learning-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Machine Learning";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Machine Learning";
      logo.style.transform = "rotate(0deg)";
    }
  });
</script>

## Tools
<a id="tools"></a>


<!-- Wakatime -->
<figure>
  <button id="toggle-wakatime" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/Logo.svg" alt="Wakatime Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Programming Languages - Show Wakatime</span>
  </button>
  <div id="wakatime-container" style="display: none; margin-top: 20px;">
    <embed src="https://wakatime.com/share/@6b618539-0e05-404e-949c-e4bd225c514b/41af378e-9a1c-4675-937b-6ba3d0330fa5.svg">
  </div>
</figure>

<!-- Libraries -->
<figure>
  <button id="toggle-libraries" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/library.svg" alt="Library Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Libraries</span>
  </button>
  <div id="library-container" style="display: none; margin-top: 20px;">
    <ul>
      <li>Pandas</li>
      <li>NumPy</li>
      <li>Scikit-learn</li>
      <li>TensorFlow</li>
      <li>Pytorch</li>
    </ul>
  </div>
</figure>

<!-- Databases -->
<figure>
  <button id="toggle-databases" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/database.svg" alt="Database Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Databases</span>
  </button>
  <div id="database-container" style="display: none; margin-top: 20px;">
    <ul>
      <li>MySQL</li>
      <li>SQLite</li>
      <li>DuckDB</li>
      <li>MariaDB</li>
    </ul>
  </div>
</figure>

<!-- Visualization and Reporting -->
<figure>
  <button id="toggle-visualization" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/visual.svg" alt="Visualization Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Visualization and Reporting</span>
  </button>
  <div id="visualization-container" style="display: none; margin-top: 20px;">
    <ul>
      <li>Streamlit</li>
      <li>Evidence</li>
    </ul>
  </div>
</figure>

<!-- Tools -->
<figure>
  <button id="toggle-tools" style="display: flex; align-items: center; border: none; background: none; cursor: pointer;">
    <img src="{{ site.baseurl }}/assets/icons/tools.svg" alt="Tools Logo" class="logo" style="width: 40px; height: 40px; margin-right: 10px;">
    <span>Tools</span>
  </button>
  <div id="tools-container" style="display: none; margin-top: 20px;">
    <ul>
      <li>Git</li>
      <li>Docker</li>
      <li>Jupyter Notebook</li>
      <li>VS Code</li>
    </ul>
  </div>
</figure>

<script>
  // Wakatime toggle
  document.getElementById("toggle-wakatime").addEventListener("click", function() {
    const container = document.getElementById("wakatime-container");
    const logo = this.querySelector(".logo");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Wakatime";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Show Wakatime";
      logo.style.transform = "rotate(0deg)";
    }
  });

  // Libraries toggle
  document.getElementById("toggle-libraries").addEventListener("click", function() {
    const container = document.getElementById("library-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Libraries";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Libraries";
      logo.style.transform = "rotate(0deg)";
    }
  });

  // Databases toggle
  document.getElementById("toggle-databases").addEventListener("click", function() {
    const container = document.getElementById("database-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Databases";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Databases";
      logo.style.transform = "rotate(0deg)";
    }
  });

  // Visualization and Reporting toggle
  document.getElementById("toggle-visualization").addEventListener("click", function() {
    const container = document.getElementById("visualization-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Visualization and Reporting";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Visualization and Reporting";
      logo.style.transform = "rotate(0deg)";
    }
  });

  // Tools toggle
  document.getElementById("toggle-tools").addEventListener("click", function() {
    const container = document.getElementById("tools-container");
    const logo = this.querySelector("img");
    const text = this.querySelector("span");

    if (container.style.display === "none") {
      container.style.display = "block";
      text.textContent = "Hide Tools";
      logo.style.transform = "rotate(360deg)";
    } else {
      container.style.display = "none";
      text.textContent = "Tools";
      logo.style.transform = "rotate(0deg)";
    }
  });
</script>

