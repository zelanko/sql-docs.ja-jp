---
title: データベース エンジン PowerShell リファレンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: 7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 17424e5a629a4161760c35d5dcc24b80aaf9c2bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205842"
---
# <a name="database-engine-powershell-reference"></a>データベース エンジン PowerShell リファレンス
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には、[!INCLUDE[ssDE](../includes/ssde-md.md)]で一般的な操作を実行するための一連の Windows PowerShell 2.0 コマンドレットが含まれています。 また、クエリ式と URN (Uniform Resource Name) は、SQL Server PowerShell パスに変換したり、 [!INCLUDE[ssDE](../includes/ssde-md.md)]で 1 つ以上のオブジェクトを指定するために使用したりできます。  
  
## <a name="database-engine-cmdlets"></a>データベース エンジンのコマンドレット  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] に含まれている [!INCLUDE[ssDE](../includes/ssde-md.md)]用のコマンドレットは比較的少ないです。 [!INCLUDE[ssDE](../includes/ssde-md.md)] を操作する PowerShell スクリプトの多くは、SQL Server PowerShell プロバイダーおよび管理オブジェクト モデルを使用します。 詳細については、「 [SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md)」を参照してください。  
  
 Windows PowerShell 環境で SQL Server コマンドレットに関するヘルプを参照する方法については、「 [SQL Server PowerShell のヘルプの参照](../powershell/sql-server-powershell.md)」を参照してください。  
  
### <a name="in-this-section"></a>このセクションの内容  
 ここでは、これらのコマンドレットについて説明します。  
  
|説明|コマンドレット|  
|-----------------|------------|  
|使用して実行できるスクリプトなどの TRANSACT-SQL および XQuery スクリプトを実行、`sqlcmd`ユーティリティ。|[Invoke-Sqlcmd コマンドレット](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|データベース エンジン オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかを評価します。|[Invoke-PolicyEvaluation コマンドレット](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a>その他のコマンドレットに関する情報  
 `Encode-Sqlname`と`Decode-Sqlname`コマンドレット ヘルプの PowerShell パスでサポートされていない文字が含まれている SQL Server 識別子を指定できます。 詳細については、「 [PowerShell での SQL Server 識別子](../powershell/sql-server-identifiers-in-powershell.md)」を参照してください。  
  
 `Convert-UrnToPath` コマンドレットを使用して、[!INCLUDE[ssDE](../includes/ssde-md.md)] オブジェクトの Unique Resource Name を SQL Server PowerShell プロバイダーのパスに変換します。 詳細については、「 [URN から SQL Server プロバイダー パスへの変換](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)」を参照してください。  
  
## <a name="query-expressions-and-unique-resource-names"></a>クエリ式および Unique Resource Name  
 クエリ式は、オブジェクト モデル階層内の 1 つまたは複数のオブジェクトを列挙する条件のセットを指定するために XPath と同様の構文を使用する文字列です。 URN (Unique Resource Name) は、単一のオブジェクトを一意に識別する特定の種類のクエリ式文字列です。 詳細については、「 [クエリ式と Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  
