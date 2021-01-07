# Loteria-Mexicana
# Proyecto final

package modelo;
import java.io.Serializable;
import java.util.ArrayList;
import java.util.Objects;
import java.util.Random;
import loteria.LOTERIA;

public class Cartilla  implements Serializable{
    private ArrayList<Carta> cartilla = new ArrayList<>();
    
    /**
     *
     */
    public Cartilla() {
        llenarCartilla();
    }

    /**
     *
     * @return
     */
    public ArrayList<Carta> getArrCartilla() {
        return cartilla;
    }

    /**
     *
     * @param cartilla
     */
    public void setCartilla(ArrayList<Carta> cartilla) {
        this.cartilla = cartilla;
    }

    @Override
    public int hashCode() {
        int hash = 7;
        hash = 59 * hash + Objects.hashCode(this.cartilla);
        return hash;
    }

    @Override
    public boolean equals(Object obj) {
        if (obj == null) {
            return false;
        }
        if (getClass() != obj.getClass()) {
            return false;
        }
        final Cartilla other = (Cartilla) obj;
        return Objects.equals(this.cartilla, other.cartilla);
    }

    private void llenarCartilla() {
        LOTERIA.cargarMazo();
        Random rd = new Random();
        int indice;
        for (int i = 0; i < 16; i++) {
            indice=rd.nextInt(52);
            Carta c = LOTERIA.mazo.get(indice);
            while(cartilla.contains(c)){
                indice=rd.nextInt(52);
                c = LOTERIA.mazo.get(indice);
            }
            cartilla.add(c);
        }
    }

    @Override
    public String toString() {
        return "Cartilla{" + "cartilla=" + cartilla + '}';
    }
    
    
    
}
