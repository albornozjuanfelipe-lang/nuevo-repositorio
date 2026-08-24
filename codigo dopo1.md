public boolean esBuenAtaque(int longitud, int latitud) {
    for (Barco b : barcos) {
        if (b.getUbicacion().getLongitud() == longitud && b.getUbicacion().getLatitud() == latitud) {
            return false;
        }
    }
    for (PortaAviones p : portaAviones) {
        if (p.getUbicacion().getLongitud() == longitud && p.getUbicacion().getLatitud() == latitud) {
            return false;
        }
    }
    return true;
}

public boolean problemaEnAire() {
    Flota oponente = null;
    for (Flota f : tablero.getFlotas()) {
        if (f != this) {
            oponente = f;
        }
    }
    if (oponente == null) {
        return false;
    }
    for (Avion propio : aviones) {
        if (propio.isEnAire()) {
            for (Avion enemigo : oponente.getAviones()) {
                if (propio.getPlaca().equals(enemigo.getPlaca())) {
                    return true;
                }
            }
        }
    }
    return false;
}

public ArrayList<Object> seranDestruidas(int longitud, int latitud) {
    ArrayList<Object> destruidas = new ArrayList<Object>();
    for (Barco b : barcos) {
        if (b.getUbicacion().getLongitud() == longitud && b.getUbicacion().getLatitud() == latitud) {
            destruidas.add(b);
        }
    }
    for (PortaAviones p : portaAviones) {
        if (p.getUbicacion().getLongitud() == longitud && p.getUbicacion().getLatitud() == latitud) {
            destruidas.add(p);
        }
    }
    for (Avion a : aviones) {
        if (!a.isEnAire() && a.getUbicacion().getLongitud() == longitud && a.getUbicacion().getLatitud() == latitud) {
            destruidas.add(a);
        }
    }
    return destruidas;
}
    }
    return destruidas;
}
