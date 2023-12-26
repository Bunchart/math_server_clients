# math_server_clients
A C-based server and client program have been developed to manage requests for K-means and Matinv calculations from the clients. The server is equipped to handle three strategies:

1. **Fork Strategy:**
   - Establishes connections by forking the process to manage communication from a specified number of clients (default: 5), ensuring that it doesn't block connections from other clients.

2. **Muxbasic Strategy:**
   - Utilizes select calls for communication, allowing the server to detect requests from each client and handle them efficiently.

3. **Muxscale Strategy:**
   - Employs an epoll instance to optimize client communications within the server.

To run the server and client:

1. Execute 'make' to build the server and client executables.
2. Start the server, indicating the port number for the socket and the desired strategy.
3. Run the client program, specifying the server's IP address and port number.
4. Send commands from the client and observe results in the 'computed_results' directory (server-side) and 'results' directory (client-side).

**Server Command:**
- Execution: `<server_executable_path> -p <port_number> -s`

**Client Commands:**
- Execution: `<client_executable_path> (-ip <ip_address> | localhost) -p <port_number>`

After connecting to the server, execute the following commands:

- **K-means:**
  - Command: `kmeans -f <kmeans_data_file> -k <number_of_clusters>`

- **Matrix Inverse:**
  - Command: `matinv -n <size_of_matrix> -I <fast | rand>`
