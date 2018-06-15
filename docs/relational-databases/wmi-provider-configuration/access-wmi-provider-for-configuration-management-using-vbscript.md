---
title: SQL Server サービスの詳細プロパティ VBScript を使用して変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
caps.latest.revision: 17
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a49cc34f92a2dd35d5f85a6013a738184d913810
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33012135"
---
# <a name="access-wmi-provider-for-configuration-management-using-vbscript"></a>VBScript を使用して構成管理の WMI プロバイダーにアクセス
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  このセクションのインストール済みインスタンスのバージョンをリストする VBScript プログラムを作成する方法について説明[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューターで実行されています。  
  
 コード例では、コンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスおよびそのバージョンをリストします。  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a>SQL Server のインストール済みインスタンスの名前およびバージョンのリスト表示  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] のメモ帳など、テキスト エディターで新しいドキュメントを開きます。 この手順の後に示すコードをコピーし、.vbs 拡張子を付けてファイルを保存します。 この例の名前を test.vbs とします。  
  
2.  VBScript の `GetObject` 関数を使用して、コンピューター管理用の WMI プロバイダーのインスタンスに接続します。 この例では、mpc という名前のリモート コンピューターに接続しますが、コンピューター名は省略してローカル コンピューター (winmgmts:root\Microsoft\SqlServer\ComputerManagement) に接続してください。 `GetObject` 関数の詳細については、VBScript リファレンスを参照してください。  
  
3.  `InstancesOf` メソッドを使用して、サービスのリストを列挙します。 サービスは、`ExecQuery` メソッドの代わりに、簡単な WQL クエリと `InstancesOf` メソッドを使用して列挙することもできます。  
  
4.  `ExecQuery` メソッドおよび WQL クエリを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール済みインスタンスの名前およびバージョンを取得します。  
  
5.  ファイルを保存します。  
  
6.  入力して、スクリプトを実行**cscript test.vbs**コマンド プロンプトでします。  
  
## <a name="example"></a>例  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
