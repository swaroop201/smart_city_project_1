# Smart City Data Processing Platform 🌆

A real-time smart city data processing platform that collects, processes, and analyzes various urban data streams including vehicle telemetry, GPS coordinates, traffic camera feeds, and weather information. The system utilizes Apache Kafka for real-time data streaming and Apache Spark for large-scale data processing.

## 🚀 Features

- Real-time vehicle tracking between London and Birmingham
- GPS data processing and analysis
- Traffic camera data integration
- Weather condition monitoring and analysis
- Scalable data processing with Apache Spark
- Data persistence to Amazon S3
- Event-driven architecture using Apache Kafka

## 🛠 Technology Stack

- **Apache Kafka**: Real-time data streaming
- **Apache Spark**: Distributed data processing
- **Python**: Primary programming language
- **AWS S3**: Data storage
- **Confluent Kafka Python Client**: Kafka producer implementation
- **PySpark**: Spark streaming and processing

## 📋 Prerequisites

- Python 3.x
- Apache Kafka
- Apache Spark
- AWS Account with S3 access
- Required Python packages:
  - confluent-kafka
  - simplejson
  - pyspark
  - boto3 (for AWS interaction)

## ⚙️ Configuration

1. Create a `config.py` file with the following structure:
```python
configuration = {
    "AWS_ACCESS_KEY": "your-aws-access-key",
    "AWS_SECRET_KEY": "your-aws-secret-key",
    "KAFKA_BOOTSTRAP_SERVERS": "localhost:9092",
    "VEHICLE_TOPIC": "vehicle_data",
    "GPS_TOPIC": "gps_data",
    "TRAFFIC_TOPIC": "traffic_data",
    "WEATHER_TOPIC": "weather_data",
    "EMERGENCY_TOPIC": "emergency_data"
}
```

2. Configure environment variables (optional):
```bash
export KAFKA_BOOTSTRAP_SERVERS=localhost:9092
export VEHICLE_TOPIC=vehicle_data
export GPS_TOPIC=gps_data
export TRAFFIC_TOPIC=traffic_data
export WEATHER_TOPIC=weather_data
```

## 🚀 Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/smart-city-project.git
cd smart-city-project
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

3. Configure AWS credentials and Kafka settings in `config.py`

## 💻 Usage

1. Start the Kafka server and create required topics:
```bash
# Create Kafka topics
kafka-topics --create --topic vehicle_data --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
kafka-topics --create --topic gps_data --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
kafka-topics --create --topic traffic_data --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
kafka-topics --create --topic weather_data --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

2. Run the data producer:
```bash
python main.py
```

3. Start the Spark streaming application:
```bash
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.13:3.5.0 spark-city.py
```

## 📊 Data Schemas

The project handles multiple data types with the following schemas:

### Vehicle Data
- ID
- Device ID
- Timestamp
- Location (latitude, longitude)
- Speed
- Direction
- Make
- Model
- Year
- Fuel Type

### GPS Data
- ID
- Device ID
- Timestamp
- Speed
- Direction
- Vehicle Type

### Traffic Camera Data
- ID
- Device ID
- Camera ID
- Location
- Timestamp
- Snapshot Data

### Weather Data
- ID
- Device ID
- Location
- Timestamp
- Temperature
- Weather Condition
- Precipitation
- Wind Speed
- Humidity
- Air Quality Index

## 📁 Project Structure

```
smart-city-project/
│
├── main.py              # Data producer and simulator
├── spark-city.py        # Spark streaming application
├── config.py            # Configuration settings
├── requirements.txt     # Python dependencies
└── README.md           # Project documentation
```

## 🔄 Data Flow

1. The system simulates a journey from London to Birmingham
2. Real-time data is generated for vehicles, GPS, traffic cameras, and weather
3. Data is published to respective Kafka topics
4. Spark streaming application processes the data
5. Processed data is stored in AWS S3 in Parquet format

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.
