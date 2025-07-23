<!-- loioe21312dfd0b845b9b8c65fd0028cc236 -->

# Replacement of the Old *Destinations* Editor with a New Set of UIs

Get information on the sunset of the old *Destinations* editor, which is replaced by a new set of UIs for destination management in the cockpit.

The *Destinations* editor, which is the administrative UI of the Destination service, has undergone a major overhaul in the last couple of years. During the second half of 2024, we started introducing some elements of the new UIs to the BTP cockpit, side by side with the existing editor:

-   Initially, we released the [Destination Trust](manage-trust-82dbeca.md) UI, used for managing the signing certificates for the assertion XML in SAML-based flows.
-   In a next step, we released the [Destination Certificates](manage-destination-certificates-df1bb55.md) page, used for managing certificates stored in the Destination service, including the generation of certificates and flagging them for auto-renewal.
-   Finally, we introduced the actual new [Destinations](using-the-destinations-editor-in-the-cockpit-565fdb3.md) UI, which we called *Destinations \(New\)* in order to separate it from the old UI. The new *Destinations* UI lets you manage the destinations themselves, including creating them from templates \(for example, from [service instances](destinations-pointing-to-service-instances-685f383.md)\).

Also, we brought these new UIs to the service instance level where applicable.

After the initial release, the new UIs received a lot of enhancements, eventually achieving feature parity with the old UI. On top of that, some new functionality is available in the new UIs. As such, we are now ready to announce the **shutdown of the old UI by end of October 2025**. Until then, the old UI will still be available under the *Destinations \(Legacy\)* navigation entry in the cockpit, while the new one is simply called *Destinations* again.

As of November 2025, the old UI will be removed from the cockpit.

