---
title: "Direct Routing country codes"
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.reviewer: NMuravlyannikov
ms.topic: reference
ms.service:  
- msteams
ms.prod: skype-for-business-itpro
localization_priority: Normal
search.appverid: MET150
ms.collection: Teams_ITAdmin_Help
appliesto:
- Microsoft Teams
description: "Read this article to locate media path country codes for Direct Routing."
---

# Direct Routing media path country codes

When choosing a routing path for media, Direct Routing, by default, always assigns a datacenter based on the public IP address of the Session Border Controller (SBC), and always selects the path closest to the SBC datacenter.

However, in some cases the default media path might not be the optimal media path; for example, a public IP from a United States range might be assigned to an SBC located in Europe. 

By using the -MediaRelayRoutingLocationOverride parameter with the New-CsOnlinePSTNGateway and Set-CsOnlinePSTNGateway cmdlets, you can specify the preferred region for media traffic. For example, the following command specifies that the preferred region is Germany:

Set-CSOnlinePSTNGateway -Identity sbc1.contoso.com –MediaRelayRoutingLocationOverride DE 

Note that Microsoft only recommends setting this parameter if the call logs clearly indicate that the default assignment of the datacenter for the media path does not use the path closest to the SBC datacenter. 
 
## Country code reference table

The following table shows the country code values for the -MediaRelayRoutingLocationOverride parameter:

| Country         | Code 
|-----------------|--------------------|
| Afghanistan     | AF |
| Aland Islands   | AX |
| Albania         | AL |
| Algeria         | DZ |
| American Samoa  | AS |
| Andorra         | AD |
| Angola          | AO |
| Anguilla        | AL |
| Antarctica      | AQ | 
| Antigua and Barbuda | AG |
| Argentina       | AR |
| Armenia         | AM |
| Aruba           | AW |
| Australia       | AU |
| Austria         | AT |
| Azerbaijan      | AZ |
| Bahamas         | BS |
| Bahrain         | BH |
| Bangladesh      | BD |
| Barbados        | BB |
| Belarus         | BY |
| Belgium         | BE |
| Belize          | BZ |
| Benin           | BJ |
| Bermuda         | BM |
| Bhutan          | BT |
| Bolivia         | BO |
| Bonaire         | BQ |
| Bosnia and Herzegovina | BA |
| Botswana        | BW |
| Bouvet Island   | BV |
| Brazil          | BR |
| British Indian Ocean Territory | IO |
| British Virgin Islands | VG |
| Brunei          | BN |
| Bulgaria        | BG |
| Burkina Faso    | BF |
| Burundi         | BI |
| Cabo Verde      | CV |
| Cambodia        | KH |
| Cameroon        | CM |
| Canada          | CA |
| Cayman Islands  | KY |
| Central African Republic | CF |
| Chad            | TD |
| Chile           | CL |
| China           | CN |
| Christmas Island | CX |
| Cocos (Keeling) Islands | CC |
| Colombia        | CO |
| Comoros         | KM |
| Congo           | CG |
| Congo (DRC)     | CD |
| Cook Islands    | CK |
| Costa Rica      | CR |
| Cote d'Ivoire   | CI |
| Croatia         | HR |
| Cuba            | CU |
| Curacao         | CW |
| Cyprus          | CY |
| Czechia         | CZ |
| Denmark         | DK |
| Djibouti        | DJ |
| Dominica        | DM |
| Dominican Republic | DO |
| Ecuador         | EC |
| Egypt           | EG |
| El Salvador     | SV |
| Equatorial Guinea | GQ |
| Eritrea         | ER |
| Estonia         | EE |
| Eswatini        | SZ |
| Ethiopia        | ET |
| Falkland Islands | FK |
| Faroe Islands   | FO |
| Fiji            | FJ |
| Finland         | FI |
| France          | FR |
| French Guiana   | GF |
| French Polynesia | PF |
| French Southern Territories | TF |
| Gabon           | GA |
| Gambia          | GM |
| Georgia         | GE |
| Germany         | DE |
| Ghana           | GH |
| Gibraltar       | GI |
| Greece          | GR |
| Greenland       | GL |
| Grenada         | GD |
| Guadeloupe      | GP |
| Guam            | GU |
| Guatemala       | GT |
| Guernsey        | GG |
| Guinea          | GN |
| Guinea-Bissau   | GW |
| Guyana          | GY |
| Haiti           | HI |
| Heard Island and McDonald Islands | HM |
| Honduras        | HN |
| Hong Kong SAR   | HK |
| Hungary         | HU |
| Iceland         | IS |
| India           | IN |
| Indonesia       | ID |
| Iran            | IR |
| Iraq            | IQ |
| Ireland         | IE |
| Isle of Man     | IM |
| Israel          | IL |
| Italy           | IT |
| Jamaica         | JM |
| Jan Mayen       | XJ |
| Japan           | JP |
| Jersey          | JE |
| Jordan          | JO |
| Kazakhstan      | KZ |
| Kenya           | KE |
| Kiribati        | KI |
| Korea           | KR |
| Kosovo          | XK |
| Kuwait          | KW |
| Kyrgyzstan      | KG |
| Laos            | LA |
| Latvia          | LV |
| Lebanon         | LB |
| Lesotho         | LS |
| Liberia         | LR |
| Libya           | LY |
| Liechtenstein   | LI |
| Lithuania       | LT |
| Luxembourg      | LU |
| Macao SAR       | MO |
| Madagascar      | MG |
| Malawi          | MW |
| Malaysia        | MY |
| Maldives        | MV |
| Mali            | ML |
| Malta           | MT |
| Marshall Islands | MH |
| Martinique      | MQ |
| Mauritania      | MR |
| Mauritius       | MU |
| Mayotte         | YT |
| Mexico          | MX |
| Micronesia      | FM |
| Moldova         | MD |
| Monaco          | MC |
| Mongolia        | MN |
| Montenegro      | ME |
| Montserrat      | MS |
| Morocco         | MA |
| Mozambique      | MZ |
| Myanmar         | MM |
| Namibia         | NA |
| Nauru           | NR |
| Nepal           | NP |
| Netherlands     | NL |
| New Caledonia   | NC |
| New Zealand     | NZ |
| Nicaragua       | NI |
| Niger           | NE |
| Nigeria         | NG |
| Niue            | NU |
| Norfolk Island  | NF |
| North Korea     | KP |
| North Macedonia | MK |
| Northern Mariana Islands | NP |
| Norway          | NO |
| Oman            | OM |
| Pakistan        | PK |
| Palau           | PW |
| Palestinian Authority | PS |
| Panama          | PA |
| Papua New Guinea | PG |
| Paraguay        | PY |
| Peru            | PE |
| Philippines     | PH |
| Pitcairn Islands | PN |
| Poland          | PL |
| Portugal        | PT |
| Puerto Rico     | PR |
| Qatar           | QA |
| Reunion         | RE |
| Romania         | RO |
| Russia          | RU |
| Rwanda          | RW |
| Saba            | XS |
| Saint Barthelemy | BL |
| Saint Kitts and Nevis | KN |
| Saint Lucia     | LC |
| Saint Martin    | MF |
| Saint Pierre and Miquelon | PM |
| Saint Vincent and the Grenadines | VC |
| Samoa           | WS |
| San Marino      | SM |
| Sao Tome and Principe | ST |
| Saudi Arabia    | SA |
| Senegal         | SN |
| Serbia          | RS |
| Seychelles      | SC |
| Sierra Leone    | SL | 
| Singapore       | SG |
| Sint Eustatius  | XE |
| Sint Maarten    | SX |
| Slovakia        | SK |
| Slovenia        | SL |
| Solomon Islands | SB |
| Somalia         | SO |
| South Africa    | ZA |
| South Georgia and South Sandwich Islands | GS |
| South Sudan     | SS |
| Spain           | ES |
| Sri Lanka       | LK |
| St Helena, Ascension, Tristan da Cunha | SH |
| Sudan           | SD |
| Suriname        | SR |
| Svalbard        | SJ |
| Sweden          | SE |
| Switzerland     | CH |
| Syria           | SY |
| Taiwan          | TW |
| Tajikistan      | TJ |
| Tanzania        | TZ |
| Thailand        | TH |
| Timor-Leste     | TL |
| Togo            | TG |
| Tokelau         | TK |
| Tonga           | TO |
| Trinidad and Tobago | TT |
| Tunisia         | TN |
| Turkey          | TR |
| Turkmenistan    | TM |
| Turks and Caicos Islands | TC |
| Tuvalu          | TV |
| U.S. Outlying Islands | UM |
| U.S. Virgin Islands | VI |
| Uganda          | UG |
| Ukraine         | UA |
| United Arab Emirates | AE |
| United Kingdom  | GB |
| United States   | US |
| Uruguay         | UY |
| Uzbekistan      | UZ |
| Vanuatu         | VU |
| Vatican City    | VA |
| Venezuela       | VE |
| Vietnam         | VN |
| Wallis and Futuna | WF |
| Yemen           | YE |
| Zambia          | ZM |
| Zimbabwe        | ZW |

