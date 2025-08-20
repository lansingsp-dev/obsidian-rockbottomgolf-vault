Screenshot of Osano consent preferences privacy dialog. 


![[Pasted image 20250724083603.png]]

Screenshot of old consent from BigCommerce

![[Pasted image 20250724090248.png]]

New Osano direct showDrawer
![[Pasted image 20250724094917.png]]


`Cookie “osano_consentmanager_expdate” has been rejected for invalid domain.`

```handlebars
{{#each pages}}
    <li>
        <a href="{{url}}">{{name}}</a>
    </li>
    {{#if (eq name "Privacy Policy")}}
        <li>
            <a href="#" onclick="Osano.cm.showDrawer('osano-cm-dom-info-dialog-open'); return false;">
                {{lang 'footer.manage_privacy'}}
            </a>
        </li>
    {{/if}}
{{/each}}
```

![[Pasted image 20250724202831.png]]

