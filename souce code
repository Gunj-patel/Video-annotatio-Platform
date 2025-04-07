import org.opencv.core.*;
import org.opencv.videoio.VideoCapture;
import org.opencv.imgproc.Imgproc;
import org.opencv.highgui.HighGui;

public class vid {
    public static void main(String[] args) {
        System.loadLibrary(Core.NATIVE_LIBRARY_NAME);

        String videoPath = "D:/star/cat.mp4";
        VideoCapture cap = new VideoCapture(videoPath);

        if (!cap.isOpened()) {
            System.out.println("Error: Cannot open video!");
            return;
        }

        Mat frame = new Mat();
        while (true) {
            if (!cap.read(frame) || frame.empty()) break;

            // Get frame dimensions
            int width = frame.cols();
            int height = frame.rows();

            // Draw a rectangle in the center
            Point topLeft = new Point(width / 4, height / 4);
            Point bottomRight = new Point(3 * width / 4, 3 * height / 4);
            Imgproc.rectangle(frame, topLeft, bottomRight, new Scalar(0, 255, 255), 4);

            // Put text at the top
            Imgproc.putText(frame, "Hi", new Point(50, 50),
                    Imgproc.FONT_HERSHEY_SIMPLEX, 1.5, new Scalar(255, 255, 255), 3);

            HighGui.imshow("Annotated Video", frame);

            if (HighGui.waitKey(30) == 'q') break;
        }

        cap.release();
        HighGui.destroyAllWindows();
    }
}
