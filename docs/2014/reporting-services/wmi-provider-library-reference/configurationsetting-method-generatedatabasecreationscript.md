---
title: GenerateDatabaseCreationScript メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
caps.latest.revision: 25
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 05560854358e95ce4beae1727e8c1aeb7be131d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072938"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserverconfigurationsetting"></a>GenerateDatabaseCreationScript メソッド (WMI MSReportServer_ConfigurationSetting)
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
>  以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 *IsSharePointMode* = `True`ためにはサポートされません SharePoint モードで[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]は SharePoint 共有サービスは WMI プロバイダーで管理されません。 常にこのパラメーターに設定する必要があります`False`です。  
  
 *[スクリプト]*  
 [out] 生成された SQL スクリプトを含む文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを使用すると、現在接続されているレポート サーバーのバージョンに対応するレポート サーバー データベースを作成する SQL スクリプトが生成されます。  
  
 *DatabaseName* パラメーターに指定する値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース名前付け規則に準拠している必要があります。  
  
 スクリプトを生成する際、このメソッドは、データベースが存在するかどうかをチェックしません。  
  
 スクリプトを生成する際、このメソッドは、レポート サーバー データベースが存在するかどうかをチェックしません。  
  
 生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  