# python-courier-tracking-code
from flask import Flask, request

app = Flask(__name__)

tracking_data = {
    "12345": {"status": "Out for delivery"},
    "67890": {"status": "Delivered"}
}

@app.route('/tracking', methods=['GET'])
def track_shipment():
    tracking_number = request.args.get('tracking_number')
    if tracking_number in tracking_data:
        return tracking_data[tracking_number]
    else:
        return {"error": "Tracking number not found"}

if __name__ == '__main__':
    app.run()

