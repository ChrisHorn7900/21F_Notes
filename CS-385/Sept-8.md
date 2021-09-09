#### **Two Assignments: Sieve of Eratosthenes and Student Class**

# Arrays

### Changes the start address of the array
    int *values = new int[x];

    for(int i = 0; i < x; i++) {
        values + i;
    }

### Different notation for accessing values inside of array using pointer
- C++ still reads array_name[index] like java, but it's good to know exactly what is going on under the hood

        for(int i = 0; i < x; i++) {
            *(values + i) = i; or values[i] = i;
        }


### Deallocates used memory
- C++ does not have it's own garbage collector like java

        delete [] values;

### Sample code for displaying the contents of an array

    void display_array(int array[], int length) {
        for(int i = 0; i < length; i++) {
            cout << array[i] << " ";
        }
        cout << endl;
    }

    display_array(values, x);

### Sample code for displaying the contents of an array pt2
- This time the same function is defined but using pointers instead of the regular syntax

        void display_array_ptr(int *array, int length) {
            for(int *p = array; p < array + length; p++) {
                cout << *p << " ";
            }
            cout << endl;
        }

# Classes
- This class utilizes and initializer list for its constructor

        class MyPoint{
            public:
                MyPoint(int x, int y, float z) : x_{x}, y_{y}, z_{z} {}

                //Methods that do not modify member vairalbes should be declared const
                void print_coords() const {
                    cout << "(x, y, z) = (" << x_ << ", " << y_ <<
                    ", " << fixed << setprecision(2) << z_ << ")" 
                    << endl;
                }

                //Mutator (setter)
                void set_x(int x) {
                    x_ = x;
                }

                //Accessors (getter), declared const
                int get_x() const {
                    return x_;
                }

            private:
                //class variables typically have '_' at the end to denote that
                //they are such
                int x_, y_;
                float z_;
        }; //classes must have a semicolon following the closing bracket

        int main() {

            //Objects allocated to the stack
            MyPoint point1(1, 2, 3.14);
            MyPoint point2(4, 5, 6.28);
            MyPoint point3(7, 8, 9);

            //vectors in c++ are like dynamic arrays in java
            vector<MyPoint> points;
            points.push_back(point1);
            points.push_back(point2);
            points.push_back(point3);

            vector<MyPoint> points_above_two;

            //for-each loop (using a reference so there isn't a copy
            of each object being made)
            for(const auto &point : points){
                //auto is in place of manually putting in datatype
                if(point.get_x() > 2){
                    points_above_two.push_back(point);
                }
            }

            //Object allocated on the heap
            //used for creating an object after compiling
            MyPoint *point4 = new MyPoint(x, y, 7);
            //Calling the method using the pointer to the object
            point4->print_coords(); // same as *(point4).print_coords()

            delete point4;
            // be sure to delete after being used to free memory on heap
            // remember there is no garbage collector
        }
