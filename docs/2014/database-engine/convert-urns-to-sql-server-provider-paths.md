---
title: URN から SQL Server プロバイダー パスへの変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e75581756f0464197e05b78083b7e90d7d3dfb3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061292"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a>URN から SQL Server プロバイダー パスへの変換
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) モデルでは、オブジェクトに対して URN (Uniform Resource Name) が作成されます。 各 URN は一意にする SMO オブジェクトを識別しを使用して SQL Server PowerShell プロバイダー パスに変換できる、`Convert-UrnToPath`コマンドレット。  
  
## <a name="converting-urns-to-paths"></a>パスへの URN の変換  
 各 URN に含まれる情報はオブジェクトへのパスと同じですが、形式が異なります。 たとえば、テーブルへのパスは次のようになります。  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 これと同じオブジェクトへの URN は次のようになります。  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 PowerShell スクリプトで SMO オブジェクトを作成した場合は、`Urn` プロパティを参照してそのオブジェクトの URN を取得し、`Convert-UrnToPath` コマンドレットを使用して SMO URN 文字列を Windows PowerShell パスに変換できます。 次に、プロバイダーを使用して、パス上の別の場所に移動できます。  
  
 Windows PowerShell パス名でサポートされない拡張文字がノード名に含まれている場合、`Convert-UrnToPath` はそれらの文字を 16 進数表記でエンコードします。 たとえば、"My:Table" は "My%3ATable" として返されます。  
  
 このコマンドレットの使用例については、Windows PowerShell で次を実行してください。  
  
```  
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a>参照  
 [クエリ式と Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md)   
 [SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  
