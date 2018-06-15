---
title: ConfigurationSetting メソッド - GenerateDatabaseCreationScript | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1b3ff8c46b9729722789ccf713ea11d86d9baf42
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33030929"
---
# <a name="configurationsetting-method---generatedatabasecreationscript"></a>ConfigurationSetting メソッド - GenerateDatabaseCreationScript
  レポート サーバー データベースの作成で使用する SQL スクリプトを生成します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *Databasename*  
 作成するレポート サーバー データベースの名前を含む文字列。  
  
 *Lcid*  
 ロール名のローカライズに使用される値。  
  
 *IsSharePointMode*  
 ネイティブ モードと SharePoint 統合モードのどちらでデータベースを作成するかを示します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降、 *IsSharePointMode*=**True** はサポートされません。SharePoint モードでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。 このパラメーターは常に **False**に設定してください。  
  
 *[スクリプト]*  
 [out] 生成された SQL スクリプトを含む文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを使用すると、現在接続されているレポート サーバーのバージョンに対応するレポート サーバー データベースを作成する SQL スクリプトが生成されます。  
  
 *DatabaseName* パラメーターに指定する値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース名前付け規則に準拠している必要があります。  
  
 スクリプトを生成する際、このメソッドは、データベースが存在するかどうかをチェックしません。  
  
 スクリプトを生成する際、このメソッドは、レポート サーバー データベースが存在するかどうかをチェックしません。  
  
 生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
