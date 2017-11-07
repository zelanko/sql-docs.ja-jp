---
title: "接続表現 (テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2fa62e16d603bb9adfff2410d14d376f358273be
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="connection-representation-tabular"></a>接続表現 (表形式)
  接続オブジェクトは、テーブル モデルに入力されるデータのソースを定義します。  
  
## <a name="connection-representation"></a>接続表現  
 接続オブジェクトの仕様は、OLE DB プロバイダーの規則に従います。  
  
### <a name="connection-in-amo"></a>AMO 内の接続  
 AMO を使用してテーブル モデル データベースを管理する場合、AMO 内の <xref:Microsoft.AnalysisServices.DataSource> オブジェクトは、接続論理オブジェクトと一対一で対応します。  
  
 次のコード スニペットは、AMO データ ソース、またはテーブル モデルの Connection オブジェクトを作成する方法を示しています。  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a>Tabular AMO 2012 サンプル  
 AMO を使用して作成して接続表現を操作する方法の理解がある、Tabular AMO 2012 サンプル; 内のソース コードを参照してください。具体的には次のソース ファイルで確認してください: Database.cs です。 このサンプルは、Codeplex から入手できます。 サンプル コードは、ここで説明する論理的概念をサポートする目的でのみ提供されるものであり、運用環境では使用しないでください。  
  
  

