class SharedBuffer {
    private int data = -1;
    private boolean isAvailable = false;

    public synchronized void produce(int data) throws InterruptedException {
        while (isAvailable) {
            wait();
        }
        this.data = data;
        System.out.println("Produced: " + data);
        isAvailable = true;
        notify();
    }

    public synchronized int consume() throws InterruptedException {
        while (!isAvailable) {
            wait();
        }
        int consumedData = data;
        System.out.println("Consumed: " + consumedData);
        isAvailable = false;
        notify();
        return consumedData;
    }
}

class Producer implements Runnable {
    private SharedBuffer buffer;

    public Producer(SharedBuffer buffer) {
        this.buffer = buffer;
    }

    @Override
    public void run() {
        int count = 1;
        while (true) {
            try {
                buffer.produce(count++);
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

class Consumer implements Runnable {
    private SharedBuffer buffer;

    public Consumer(SharedBuffer buffer) {
        this.buffer = buffer;
    }

    @Override
    public void run() {
        while (true) {
            try {
                buffer.consume();
                Thread.sleep(1500);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}

public class IPCExample {
    public static void main(String[] args) {
        SharedBuffer buffer = new SharedBuffer();

        Thread producerThread = new Thread(new Producer(buffer));
        Thread consumerThread = new Thread(new Consumer(buffer));

        producerThread.start();
        consumerThread.start();
    }
}
