# hm-6
import org.junit.Test;
import static org.junit.Assert.*;
import static org.mockito.Mockito.*;

public class TICTACTOETest {

    @Test
    public void testEstGagnant() {
        TICTACTOE jeu = new TICTACTOE();
        jeu.setJoueur('X'); // Set the player to X for testing

        // Create a mock tableau with a winning scenario for X
        char[][] mockTableau = {
            {'X', ' ', ' '},
            {'X', ' ', ' '},
            {'X', ' ', ' '}
        };

        jeu.setTableau(mockTableau);

        // Now X should be the winner
        assertTrue(jeu.estgagnant());
    }

    @Test
    public void testEstMatchNul() {
        TICTACTOE jeu = new TICTACTOE();

        // Create a mock tableau with no empty spaces
        char[][] mockTableau = {
            {'X', 'O', 'X'},
            {'X', 'X', 'O'},
            {'O', 'X', 'O'}
        };

        jeu.setTableau(mockTableau);

        // Since there are no empty spaces, it should be a draw
        assertTrue(jeu.estmatchnul());
    }

    @Test
    public void testJouerTour() {
        TICTACTOE jeu = new TICTACTOE();

        // Mock a Scanner object to provide predefined inputs
        Scanner mockScanner = mock(Scanner.class);
        when(mockScanner.nextInt()).thenReturn(1, 1); // Always return 1 for both row and column

        // Replace the standard input with the mock Scanner
        System.setIn(new ByteArrayInputStream("1\n1\n".getBytes()));

        // Play a turn
        jeu.jouerTour();

        // Check if the tableau is updated correctly
        assertEquals('X', jeu.getTableau()[1][1]);
    }
}
