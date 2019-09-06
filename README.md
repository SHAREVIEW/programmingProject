https://csharp.hotexamples.com/examples/InTheHand.Net.Sockets/BluetoothClient/Connect/php-bluetoothclient-connect-method-examples.html

EXAMPLE #3


# programmingProject

File: Bluetooth.cs  Project: donnaknew/programmingProject
        /// <summary>
        /// Attempt to connect to the BluetoothDevice, without trying to pair first.
        /// </summary>
        /// <param name="device"></param>
        /// <returns></returns>
        public static async Task<Boolean> connectToDeviceWithoutPairing(BluetoothDevice device) {
            BluetoothEndPoint endPoint = new BluetoothEndPoint(device.btDeviceInfo.DeviceAddress, BluetoothService.SerialPort);
            BluetoothClient client = new BluetoothClient();
            if (!device.Authenticated) {
                return false;
            }
            else {
                try {
                    client.Connect(endPoint);

                    if (devicesStreams.Keys.Contains(device)) {
                        devicesStreams.Remove(device);
                    }
                    devicesStreams.Add(device, client.GetStream());

                    if (devicesClients.Keys.Contains(device)) {
                        devicesClients.Remove(device);
                    }
                    devicesClients.Add(device, client);
                }
                catch (Exception ex) {
                    //System.Console.Write("Could not connect to device: " + device.DeviceName + " " + device.DeviceAddress);
                    return false;
                }
                return true;
            }
        }
