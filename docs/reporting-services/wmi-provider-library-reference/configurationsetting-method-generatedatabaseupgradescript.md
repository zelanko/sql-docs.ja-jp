---
title: "GenerateDatabaseUpgradeScript メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- GenerateDatabaseUpgradeScript method
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 87cfa22266bb876b05fd7f7387de33791e88ce21
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---generatedatabaseupgradescript"></a>GenerateDatabaseUpgradeScript ConfigurationSetting メソッド
  レポート サーバー データベースを [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] スキーマにアップグレードする場合に使用できるスクリプトを生成します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *Databasename*  
 更新するレポート サーバー データベースの名前を含む文字列。  
  
 *ServerVersion*  
 レポート サーバーのバージョンを表す文字列。  
  
 *[スクリプト]*  
 [out] 生成された SQL スクリプトを含む文字列。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>解説  
 生成されたスクリプトは、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、および [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]をサポートします。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  

