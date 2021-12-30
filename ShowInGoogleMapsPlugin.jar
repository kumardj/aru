/*
 * This software is provided "AS IS" without a warranty of any kind. You use it
 * on your own risk and responsibility!!! This file is shared under BSD v3
 * license. See readme.txt and BSD3 file for details.
 */

package kendzi.josm.plugin.google.maps;

import kendzi.josm.plugin.google.maps.action.ShowInGoogleMapsAction;

import org.openstreetmap.josm.Main;
import org.openstreetmap.josm.gui.MainMenu;
import org.openstreetmap.josm.plugins.Plugin;
import org.openstreetmap.josm.plugins.PluginInformation;

/**
 * 
 * @author Tomasz Kędziora (Kendzi)
 */
public class ShowInGoogleMapsPlugin extends Plugin {
    public ShowInGoogleMapsPlugin(PluginInformation info) {
        super(info);
        MainMenu.add(Main.main.menu.dataMenu, new ShowInGoogleMapsAction());
    }
}
