Web traffic, in this case via 80 and 8080 (HTTP alternative), is completely normal to web servers and can be allowed.  However, to deny traffic from an IP, port, or protocol, the deny needs to be selected.  Finally, at the end of a firewall table, it is in the best interest of most organizations to add an implicit deny to catch all traffic that isn't caught by the other rules.