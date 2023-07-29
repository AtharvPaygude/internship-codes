# internship-codes
#it is first project of nqueens
import java.util.*;
import java.util.Scanner;
public class nQueensProb {
    
    private static void solveQueen(int n){
        //it will store col position for each row
        int board[] = new int[n];

        placeQueen(board, 0, n);
    }

    private static boolean isSafe(int board[], int row, int col, int n){
        for(int i=0; i<row; i++){
            if(board[i]==col || board[i]-i== col-row || board[i]+i == col+row){
                return false;
            }
        }

        //safe position that's why returning true
        return true;
    }

    private static void placeQueen(int board[], int row, int n){
        //base condition
        if(row==n){
            //we have reached at last row that means we have succefully allocated col for each row
            printBoard(board, n);
        }

        else{
            for(int col=0; col<n; col++){
                if(isSafe(board, row, col, n)){
                    //store safe col for particular row
                    board[row] = col;

                    //move to next row
                    placeQueen(board, row+1, n);
                }
            }
        }

    }

    private static void printBoard(int board[], int n){
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                if(board[i]==j){
                    System.out.print(" Q ");
                }else{
                    System.out.print(" . ");
                }
            }
            System.out.println();
        }
    }

    
    public static void main(String[] args) {
        solveQueen(4);
    }
}
