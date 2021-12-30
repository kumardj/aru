/*
 * This software is provided "AS IS" without a warranty of any kind. You use it
 * on your own risk and responsibility!!! This file is shared under BSD v3
 * license. See readme.txt and BSD3 file for details.
 */
package kendzi.josm.plugin.google.maps.ui;

/**
 * Open dialog with confirmation.
 * 
 * @author Tomasz Kedziora (Kendzi)
 * 
 */
public class ShowInGoogleMapsDialogAction extends ShowInGoogleMapsDialog {

    private static final long serialVersionUID = 1L;

    private boolean runBrowser;

    @Override
    protected void onOk() {
        runBrowser = true;
        dispose();
    }

    public boolean isRunBrowser() {
        return runBrowser;
    }
}
