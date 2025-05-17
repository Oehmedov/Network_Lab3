# Network_Lab3
### There's our Python code:
    import socket

    def run_tcp_server():
        # Create a TCP/IP socket
        server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    
        # Bind the socket to the port
        server_address = ('localhost', 5050)
        print(f"Starting server on {server_address[0]}:{server_address[1]}")
        server_socket.bind(server_address)
    
        # Listen for incoming connections (only 1 connection in queue)
        server_socket.listen(1)
    
        try:
            print("Waiting for a connection...")
            # Accept a single connection
            connection, client_address = server_socket.accept()
            print(f"Connection from {client_address}")
        
            try:
                # Receive the data
                data = connection.recv(1024)
                print(f"Received: {data.decode()}")
            
                if data:
                    # Send response
                    response = "Received your message"
                    connection.sendall(response.encode())
                else:
                    print("No data received")
                
            finally:
                # Clean up the connection
                connection.close()
                print("Connection closed")
            
        finally:
            # Clean up the server socket
            server_socket.close()
            print("Server shutdown")

    if __name__ == "__main__":
        run_tcp_server()

When we run the code, we see:
![{D450C1D5-869C-42E3-A491-AC1CF2630BEA}](https://github.com/user-attachments/assets/18a09a22-073e-45b0-bc41-e11d72ef4bf1)

And by using Telnet we can see the response:
![{5E75BF3A-A589-4487-B8C8-D3C19E4BA7A7}](https://github.com/user-attachments/assets/ef5697d2-902b-4266-98d2-f866993f1a85)
![{E59BBA2F-1171-4193-8B30-55A1E772AA17}](https://github.com/user-attachments/assets/59cb0106-8583-4514-b101-864940ee4141)
![{CF39C0AE-07C0-4930-BB11-8A12C13A4F06}](https://github.com/user-attachments/assets/ded96370-3456-46b3-bee1-d20b650ca88d)
