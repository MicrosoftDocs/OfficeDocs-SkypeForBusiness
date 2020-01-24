<table>
<thead>
<tr class="header">
<th><strong>Network optimization task</strong></th>
<th><strong>Details</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Network planner</td>
<td><p>For help assessing your network, including bandwidth calculations and network requirements across your org’s physical locations, check out the <a href="network-planner.md">Network Planner</a> tool, in the <a href="https://admin.teams.microsoft.com">Teams admin center</a>. When you provide your network details and Teams usage, the Network Planner calculates your network requirements for deploying Teams and cloud voice across your organization’s physical locations.</p>
<p>For an example scenario, see <a href="tutorial-network-planner-example.md">Using Network Planner - example scenario</a>.</p></td>
</tr>
<tr class="even">
<td>Advisor for Teams</td>
<td><a href="use-advisor-teams-roll-out.md">Advisor for Teams</a> is part of the <a href="https://admin.teams.microsoft.com">Teams admin center</a>. It assesses your Office 365 environment and identifies the most common configurations that you may need to update or modify before you can successfully roll out Teams.</td>
</tr>
<tr class="odd">
<td>External Name Resolution</td>
<td>Be sure that all computers running the Teams client can resolve external DNS queries to discover the services provided by Office 365 and that your firewalls are not preventing access. For information about configuring firewall ports, go to <a href="office-365-urls-ip-address-ranges.md">Office 365 URLs and IP ranges</a>.</td>
</tr>
<tr class="even">
<td>Network Assessment Tool</td>
<td><p>Use the <a href="https://www.microsoft.com/download/details.aspx?id=53885">Network Assessment Tool</a> to test network connectivity to all IP addresses and ports used in Teams calls and meetings. Download the tool and see Usage.docx for details about how to use the tool and interpret the test results. We recommend that you run the tool from a client PC in each location where Teams will be used.</p>
<p><strong>REVIEWERS: This tool is still branded for Skype for Business. Siunie says she’s planning to update this tool for Teams, possibly in H2FY20.</strong></p></td>
</tr>
<tr class="odd">
<td>Validate (NAT) pool size</td>
<td>Validate the network address translation (NAT) pool size required for user connectivity. When multiple users and devices access Office 365 using <a href="https://docs.microsoft.com/office365/enterprise/nat-support-with-office-365?redirectSourcePath=%252farticle%252fNAT-support-with-Office-365-170e96ea-d65d-4e51-acac-1de56abe39b9">Network Address Translation (NAT) or Port Address Translation (PAT)</a>, you need to ensure that the devices hidden behind each publicly routable IP address do not exceed the supported number. Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.</td>
</tr>
<tr class="even">
<td>Routing to Microsoft data centers</td>
<td><a href="https://docs.microsoft.com/office365/enterprise/client-connectivity?redirectSourcePath=%252farticle%252fClient-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b">Implement the most efficient routing to Microsoft data centers</a>. Identify locations that can use local or regional egress points to connect to the Microsoft network as efficiently as possible.</td>
</tr>
<tr class="odd">
<td><h3 id="intrusion-detection-and-prevention-guidance">Intrusion Detection and Prevention Guidance</h3></td>
<td>If your environment has an <a href="https://docs.microsoft.com/azure/network-watcher/network-watcher-intrusion-detection-open-source-tools">Intrusion Detection</a> or Prevention System (IDS/IPS) deployed for an extra layer of security for outbound connections, be sure to whitelist all Office 365 URLs.</td>
</tr>
<tr class="even">
<td><h3 id="configure-split-tunnel-vpn">Configure split-tunnel VPN</h3>
<h3 id="section"></h3></td>
<td><p>We recommend that you provide an alternate path for Teams traffic that bypasses the virtual private network (VPN), commonly known as split-tunnel VPN. Split tunneling means that traffic for Office 365 doesn’t go through the VPN but instead goes directly to Office 365. Bypassing your VPN will have a positive impact on Teams quality, and it reduces load from the VPN devices and the organization’s network. To implement a split-tunnel VPN, work with your VPN vendor.</p>
<p>Other reasons why we recommend bypassing the VPN: VPNs are typically not designed or configured to support real-time media. Some VPNs might also not support UDP (which is required for Teams). VPNs also introduce an extra layer of encryption on top of media traffic that’s already encrypted. Connectivity to Teams might not be efficient due to hair-pinning traffic through a VPN device.</p></td>
</tr>
<tr class="odd">
<td><h3 id="implement-qos">Implement QoS</h3>
<h3 id="section-1"></h3></td>
<td><a href="qos-in-teams.md">Use Quality of Service (QoS)</a> to configure packet prioritization. This will improve call quality in Teams and help you monitor and troubleshoot call quality. QoS should be implemented on all segments of a managed network. Even when a network has been adequately provisioned for bandwidth, QoS provides risk mitigation in the event of unanticipated network events. With QoS, voice traffic is prioritized so that these unanticipated events don’t negatively affect quality.</td>
</tr>
<tr class="even">
<td><h3 id="optimize-wifi">Optimize WiFi</h3>
<h3 id="section-2"></h3></td>
<td><p>Similar to VPN, WiFi networks aren’t necessarily designed or configured to support real-time media. Planning for, or optimizing, a WiFi network to support Teams is an important consideration for a high-quality deployment. Consider these factors:</p>
<ul>
<li><p>Implement QoS or WiFi Multimedia (WMM) to ensure that media traffic is getting prioritized appropriately over your WiFi networks.</p></li>
<li><p>Plan and optimize the WiFi bands and access point placement. The 2.4 GHz range might provide an adequate experience depending on access point placement, but access points are often affected by other consumer devices that operate in that range. The 5 GHz range is better suited to real-time media due to its dense range, but it requires more access points to get sufficient coverage. Endpoints also need to support that range and be configured to leverage those bands accordingly.</p></li>
<li><p>If you’re using dual-band WiFi networks, consider implementing band steering. <em>Band steering</em> is a technique implemented by WiFi vendors to influence dual-band clients to use the 5 GHz range.</p></li>
<li><p>When access points of the same channel are too close together, they can cause signal overlap and unintentionally compete, resulting in a bad experience for the user. Ensure that access points that are next to each other are on channels that don’t overlap.</p></li>
</ul>
<p>Each wireless vendor has its own recommendations for deploying its wireless solution. Consult your WiFi vendor for specific guidance.</p></td>
</tr>
<tr class="odd">
<td><p>Monitor your network using CQD and call analytics</p>
<h3 id="section-3"></h3></td>
<td>Use the <a href="turning-on-and-using-call-quality-dashboard.md">Call Quality Dashboard (CQD)</a> to gain insight into the quality of calls made by using Teams. CQD is designed to help you optimize your network and keep a close eye on quality, reliability, and the user experience. CQD looks at aggregate telemetry for an entire organization where overall patterns can become apparent, allowing staff to make informed assessments and plan remediation activities to maximize impact. Additionally, CQD provides reports of metrics that provide insight into overall quality, reliability, and user experience. To investigate call problems for individual users, use <a href="set-up-call-analytics.md">per-user call analytics</a>.</td>
</tr>
</tbody>
</table>
