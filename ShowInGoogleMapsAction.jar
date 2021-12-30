/*
 * This software is provided "AS IS" without a warranty of any kind. You use it
 * on your own risk and responsibility!!! This file is shared under BSD v3
 * license. See readme.txt and BSD3 file for details.
 */

package kendzi.josm.plugin.google.maps.action;

import static org.openstreetmap.josm.tools.I18n.*;

import java.awt.Desktop;
import java.awt.event.ActionEvent;
import java.awt.event.KeyEvent;
import java.net.URI;
import java.util.Collection;

import javax.swing.JOptionPane;
import javax.swing.WindowConstants;

import kendzi.josm.plugin.google.maps.ui.ShowInGoogleMapsDialogAction;

import org.openstreetmap.josm.Main;
import org.openstreetmap.josm.actions.JosmAction;
import org.openstreetmap.josm.data.coor.LatLon;
import org.openstreetmap.josm.data.osm.Node;
import org.openstreetmap.josm.data.osm.OsmPrimitive;
import org.openstreetmap.josm.data.osm.Way;
import org.openstreetmap.josm.tools.Shortcut;

public class ShowInGoogleMapsAction extends JosmAction {

    /**
     * 
     */
    private static final long serialVersionUID = 1L;

    public ShowInGoogleMapsAction() {
        super(tr("Show in Google Maps"), "show-in-gmaps.png", tr(""), Shortcut.registerShortcut("tools:ShowInGoogleMaps",
                tr("Tool: {0}", tr("Show in Google Maps")), KeyEvent.VK_K, Shortcut.SHIFT), true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {

        Collection<OsmPrimitive> selectedPrimitive = Main.main.getCurrentDataSet().getSelectedNodesAndWays();

        LatLon latLon = getCoorFromSelection(selectedPrimitive);

        if (latLon == null) {
            JOptionPane.showMessageDialog(null, tr("Choose one node or way"), "Error", JOptionPane.ERROR_MESSAGE);
            return;
        }

        String url = formatGoogleUrl(latLon);

        try {
            ShowInGoogleMapsDialogAction dialog = new ShowInGoogleMapsDialogAction();

            dialog.setDefaultCloseOperation(WindowConstants.DISPOSE_ON_CLOSE);
            dialog.setVisible(false);
            dialog.setModal(true);
            dialog.setVisible(true);

            if (dialog.isRunBrowser()) {

                final Desktop desktop = Desktop.getDesktop();

                desktop.browse(new URI(url));
            }

        } catch (RuntimeException ee) {
            ee.printStackTrace();
            throw ee;
        } catch (Exception ee) {
            ee.printStackTrace();
            throw new RuntimeException(ee);
        }
    }

    private LatLon getCoorFromSelection(Collection<OsmPrimitive> selectedPrimitive) {
        if (selectedPrimitive.size() < 1) {
            return null;
        }
        OsmPrimitive primitive = selectedPrimitive.iterator().next();
        if (primitive instanceof Node) {
            Node node = (Node) primitive;
            return node.getCoor();

        } else if (primitive instanceof Way) {
            Way way = (Way) primitive;

            if (way.getNodesCount() > 0) {
                return way.getNode(0).getCoor();
            }
        }
        return null;
    }

    public static void main(String[] args) {
        double d = 12.444;

        System.out.println();
    }

    private String formatGoogleUrl(LatLon latLon) {
        // https://maps.google.pl/?ll=51.950695,15.458547
        return String.format("https://maps.google.pl/?ll=%s,%s&z=19", formatNumber(latLon.lat()), formatNumber(latLon.lon()));
    }

    private String formatNumber(double number) {
        return String.format("%.6f", number).replaceAll(",", ".");
    }

    @Override
    protected void updateEnabledState() {
        setEnabled(getCurrentDataSet() != null);
    }
}
