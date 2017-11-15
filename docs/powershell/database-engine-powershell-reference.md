---
title: "データベース エンジン PowerShell リファレンス | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c1d105c439e17f3ac3c241e9fccf6c5cfa066f7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="database-engine-powershell-reference"></a>データベース エンジン PowerShell リファレンス
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には、 [!INCLUDE[ssDE](../includes/ssde-md.md)]で一般的な操作を実行するための一連の Windows PowerShell コマンドレットが含まれています。 また、クエリ式と URN (Uniform Resource Name) は、SQL Server PowerShell パスに変換したり、 [!INCLUDE[ssDE](../includes/ssde-md.md)]で 1 つ以上のオブジェクトを指定するために使用したりできます。  
  
## <a name="database-engine-cmdlets"></a>データベース エンジンのコマンドレット  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] に含まれている [!INCLUDE[ssDE](../includes/ssde-md.md)]用のコマンドレットは比較的少ないです。 [!INCLUDE[ssDE](../includes/ssde-md.md)] を操作する PowerShell スクリプトの多くは、SQL Server PowerShell プロバイダーおよび管理オブジェクト モデルを使用します。 詳細については、「 [SQL Server PowerShell プロバイダー](../relational-databases/scripting/sql-server-powershell-provider.md)」を参照してください。  
  
 Windows PowerShell 環境で SQL Server コマンドレットに関するヘルプを参照する方法については、「 [SQL Server PowerShell のヘルプの参照](../relational-databases/scripting/get-help-sql-server-powershell.md)」を参照してください。  
  
### <a name="in-this-section"></a>このセクションの内容  
 ここでは、これらのコマンドレットについて説明します。  
  
|説明|コマンドレット|  
|-----------------|------------|  
|**sqlcmd** ユーティリティを使用して実行できるスクリプトなど、Transact-SQL スクリプトと XQuery スクリプトを実行します。|[Invoke-Sqlcmd コマンドレット](../powershell/invoke-sqlcmd-cmdlet.md)|  
|データベース エンジン オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかを評価します。|[Invoke-PolicyEvaluation コマンドレット](../powershell/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a>その他のコマンドレットに関する情報  
 **Encode-Sqlname** コマンドレットと **Decode-Sqlname** コマンドレットでは、PowerShell パスではサポートされていない文字を含んだ SQL Server 識別子を指定できます。 詳細については、「 [PowerShell での SQL Server 識別子](../relational-databases/scripting/sql-server-identifiers-in-powershell.md)」を参照してください。  
  
 **Convert-UrnToPath** コマンドレットを使用して、 [!INCLUDE[ssDE](../includes/ssde-md.md)] オブジェクトの Unique Resource Name を SQL Server PowerShell プロバイダーのパスに変換します。 詳細については、「 [URN から SQL Server プロバイダー パスへの変換](../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md)」を参照してください。  
  
## <a name="query-expressions-and-unique-resource-names"></a>クエリ式および Unique Resource Name  
 クエリ式は、オブジェクト モデル階層内の 1 つまたは複数のオブジェクトを列挙する条件のセットを指定するために XPath と同様の構文を使用する文字列です。 URN (Unique Resource Name) は、単一のオブジェクトを一意に識別する特定の種類のクエリ式文字列です。 詳細については、「 [クエリ式と Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  
