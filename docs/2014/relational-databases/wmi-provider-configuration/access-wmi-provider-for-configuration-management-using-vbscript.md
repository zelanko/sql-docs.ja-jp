---
title: VBScript を使用して SQL Server サービスの詳細プロパティを変更する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f3a380f80b4ecc7540e29605543722edd55e226d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62705063"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a>VBScript を使用して SQL Server サービスの詳細プロパティを変更する
  このセクションでは、コンピューター上で実行されているの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール済みインスタンスのバージョンを一覧表示する VBScript プログラムを作成する方法について説明します。  
  
 コード例では、コンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスおよびそのバージョンをリストします。  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>SQL Server のインストール済みインスタンスの名前およびバージョンのリスト表示  
  
1.  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] のメモ帳など、テキスト エディターで新しいドキュメントを開きます。 この手順の後に示すコードをコピーし、.vbs 拡張子を付けてファイルを保存します。 この例の名前を test.vbs とします。  
  
2.  VBScript の `GetObject` 関数を使用して、コンピューター管理用の WMI プロバイダーのインスタンスに接続します。 この例では、mpc という名前のリモート コンピューターに接続しますが、コンピューター名は省略してローカル コンピューター (winmgmts:root\Microsoft\SqlServer\ComputerManagement) に接続してください。 
  `GetObject` 関数の詳細については、VBScript リファレンスを参照してください。  
  
3.  
  `InstancesOf` メソッドを使用して、サービスのリストを列挙します。 サービスは、`ExecQuery` メソッドの代わりに、簡単な WQL クエリと `InstancesOf` メソッドを使用して列挙することもできます。  
  
4.  
  `ExecQuery` メソッドおよび WQL クエリを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール済みインスタンスの名前およびバージョンを取得します。  
  
5.  ファイルを保存します。  
  
6.  コマンドプロンプトで「」 `cscript test.vbs`と入力して、スクリプトを実行します。  
  
## <a name="example"></a>例  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
