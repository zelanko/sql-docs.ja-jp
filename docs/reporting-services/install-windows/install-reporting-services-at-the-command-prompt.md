---
title: "コマンド プロンプトでの Reporting Services のインストール |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command line
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f2c8586ba26169bdd236f825b9f9688106788fff
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="install-reporting-services-at-the-command-prompt"></a>コマンド プロンプトでの Reporting Services のインストール

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、SQL Server セットアップ プログラムからのコマンド ライン インストールをサポートしています。 このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]用のコマンド ラインからのインストール例をいくつか示します。 すべての SQL Server コンポーネントに使用できるコマンド ライン オプションの詳しい説明については、「 [コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」をご覧ください。 このトピックでは、SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインのコマンド ライン オプションについては説明していません。 アドインのコマンド インストールについては、「 [rsSharePoint.msi インストール ファイルを使用したアドインのインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint)」をご覧ください。

##  <a name="bkmk_native_mode"></a> ネイティブ モードの Reporting Services

### <a name="rsinstallmode-native-mode"></a>RSINSTALLMODE (ネイティブ モード)
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールするための主な入力設定は、 **/RSINSTALLMODE** の入力設定です。 この設定には、 **DefaultNativeMode** および **FilesOnlyMode**という 2 つのオプションがあります。  
  
 インストールに SQL Server データベース エンジンが含まれている場合、既定の RSINSTALLMODE は DefaultNativeMode です。インストールに SQL Server データベース エンジンが含まれていない場合、既定の RSINSTALLMODE は FilesOnlyMode です。インストールに SQL Server データベース エンジンが含まれていない場合に DefaultNativeMode を選択すると、そのインストールでは自動的に RSINSTALLMODE が FilesOnlyMode に変更されます。 入力設定の詳細については、「 [コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」をご覧ください。

### <a name="examples-of-native-mode-installation"></a>ネイティブ モード インストールの例

 次の例では、以下をインストールしてそれ用にアカウントを構成します。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (ネイティブ モード)。  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。  
  
-   SQL Server エージェント。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプション機能用に必要です。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]用のコマンド ラインからのインストール例をいくつか示します。  
  
```  
Setup.exe /q /IACCEPTSQLSERVERLICENSETERMS /ACTION="install" /ERRORREPORTING=1 /UPDATEENABLED="False" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Adv_SSMS,RS" /RSINSTALLMODE="DefaultNativeMode" /SQLSVCACCOUNT="[DOMAIN\ACCOUNT]" /SQLSVCPASSWORD="[PASSWORD]" /AGTSVCACCOUNT="[DOMAIN\ACCOUNT]" /AGTSVCPASSWORD="[PASSWORD]" /SQLSYSADMINACCOUNTS="[DOMAIN\ACCOUNT]"  
```  
  
##  <a name="bkmk_sharepoint_mode"></a> SharePoint モードの Reporting Services  
  
### <a name="rsshpinstallmode-sharepoint-mode"></a>RSSHPINSTALLMODE (SharePoint モード)  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を SharePoint モードでインストールするための入力設定は、 **/RSSHPINSTALLMODE**です。 入力設定には 1 つのオプション SharePointFilesOnlyMode があります。 このオプションにより、SharePoint モードに必要なすべてのファイルがインストールされますが、インストール後に構成が必要です。 追加の構成の手順は、SharePoint サーバーの全体管理を使用して行います。 詳細については、「 [SharePoint モードでの最初のレポート サーバーのインストール](http://msdn.microsoft.com/en-us/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538)」を参照してください。  
  
### <a name="examples-of-sharepoint-mode-installation"></a>SharePoint モード インストールの例  
 次の例は、SQL Server のデータベース エンジン サービス、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、および SharePoint 用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン (RS_SHPWFE) をインストールします。  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 次の例は、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のみをインストールします。  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="[PASSWORD]" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
### <a name="examples-of-sharepoint-mode-upgrade"></a>SharePoint モード アップグレードの例  
 次の例は、SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードします。 **RSUPGRADEPASSWORD** は、既存のレポート サーバー サービス アカウントのパスワードです。 RSUPGRADEPASSWORD は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アカウントがビルトイン アカウントである場合を除いて、アップグレード シナリオの必須フィールドです。  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[PASSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="[PASSWORD]"  
```  
  
 次の例を使用すると、SharePoint 共有サービス アーキテクチャに基づく SharePoint モードのインストールをアップグレードできます。 この例は ALLOWUPGRADEFORSSRSSHAREPOINTMODE スイッチを使用します。 共有サービス アーキテクチャに基づいていない古いバージョンのアップグレードの場合、スイッチは必要ありません。  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="[PASSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```

## <a name="next-steps"></a>次の手順

[コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
[SysPrep パラメーター](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md#SysPrep)   
[コマンド プロンプトからの Power Pivot をインストールします。](http://msdn.microsoft.com/en-us/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
