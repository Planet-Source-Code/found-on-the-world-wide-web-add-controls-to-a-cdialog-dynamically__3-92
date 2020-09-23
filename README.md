<div align="center">

## Add controls to a CDialog dynamically


</div>

### Description

Add controls to a CDialog dynamically--instead of using a dialog resource.

You can add controls to your dialog dynamically by using methods CWnd::Create() and CWnd::CreateEx() or overridables of CWnd::Create() in control window wrapper classes such as CEdit or CListbox, etc.

DEMPSEY@DEMPSEY.COM
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Found on the World Wide Web](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/found-on-the-world-wide-web.md)
**Level**          |Unknown
**User Rating**    |4.0 (8 globes from 2 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__3-3.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/found-on-the-world-wide-web-add-controls-to-a-cdialog-dynamically__3-92/archive/master.zip)





### Source Code

```
. For example, to create CEdit control, you can do the following:
1) add a member variable m_ec_myedit to your dialog .h file;
2) I assume that your dialog templete has some control with ID = IDC_ABOVE_DYNAMIC_EDIT, and you want your dynamically created edit control to have the same width and be placed under IDC_ABOVE_DYNAMIC_EDIT. Then add the following code under the call to CDialog::OnInitDialog() in your overriden OnInitDialog():
GetDlgItem(IDC_ABOVE_DYNAMIC_EDIT)->GetWindowRect(rect);
ScreenToClient(rect);
CRect rectNew(rect.left, rect.bottom+5, rect.right, rect.bottom+35);
m_myEdit.CreateEx(WS_EX_CLIENTEDGE, "EDIT", NULL
/*lpszWindowName*/,
WS_CHILD|WS_VISIBLE|WS_GROUP|WS_TABSTOP|WS_BORDER, rectNew.left, rectNew.top,
rectNew.Width(), rectNew.Height(), this->GetSafeHwnd(), NULL, NULL);
m_myEdit.ShowWindow(SW_SHOW);
It's that simple. The only thing that differs for different control classes is window styles. Usually, you can find the most important of style and extended style constants in online help.
```

