---
title: SQL Server PowerShell プロバイダーでのインスタンスの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
ms.openlocfilehash: b23c2f331c681862f7b871521937847eec2d9419
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960130"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a>SQL Server PowerShell プロバイダーでのインスタンスの指定
  SQL Server PowerShell プロバイダーに指定するパスでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスと、それが実行されているコンピューターを示す必要があります。 コンピューターおよびインスタンスを指定する構文は、SQL Server 識別子と Windows PowerShell パスの両方の規則に準拠している必要があります。  
  
1.  **作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)  
  
2.  **インスタンスの指定方法:**  [使用例](#Examples)  
  
## <a name="before-you-begin"></a>はじめに  
 SQL Server プロバイダーのパスで SQLSERVER:\SQL に続く最初のノードは、たとえば次のような、 [!INCLUDE[ssDE](../includes/ssde-md.md)]のインスタンスが実行されているコンピューターの名前です。  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 [!INCLUDE[ssDE](../includes/ssde-md.md)]のインスタンスと同じコンピューター上で Windows PowerShell を実行している場合は、コンピューター名の代わりに localhost または (local) を使用できます。 localhost または (local) が使用されたスクリプトは、異なるコンピューター名を反映するための変更を加えることなく、すべてのコンピューター上で実行できます。  
  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] の実行可能プログラムの複数のインスタンスを、同じコンピューターで実行できます。 SQL Server プロバイダーのパスでコンピューター名に続くノードは、たとえば次のように、インスタンスを識別します。  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 各コンピューターでは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]の既定のインスタンスを 1 つだけ使用できます。 既定のインスタンスには、そのインストール時に名前を指定しません。 接続文字列にコンピューター名のみを指定すると、そのコンピューターの既定のインスタンスに接続されます。 コンピューター上のその他すべてのインスタンスは、名前付きインスタンスにする必要があります。 インスタンス名はセットアップ時に指定します。接続文字列には、コンピューター名とインスタンス名の両方を指定する必要があります。  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 PowerShell スクリプトでは、ピリオド (.) を使用してローカル コンピューターを指定することはできません。 PowerShell ではピリオドはコマンドとして解釈されるため、ピリオドはサポートされません。  
  
 通常、(local) に使用されているかっこ文字は、Windows PowerShell でコマンドとして扱われます。 パス内で使用するには、エンコードするかエスケープする必要があります。または、パスを二重引用符で囲みます。 詳細については、「SQL Server 識別子のエンコードとデコード」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーでは、常にインスタンス名を指定する必要があります。 既定のインスタンスには、DEFAULT というインスタンス名を指定する必要があります。  
  
##  <a name="examples-computer-and-instance-names"></a><a name="Examples"></a>例コンピューター名とインスタンス名  
 この例では、次のように、localhost および DEFAULT を使用してローカル コンピューター上の既定のインスタンスを指定します。  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 通常、(local) に使用されているかっこ文字は、Windows PowerShell でコマンドとして扱われます。 次のいずれかの作業を行う必要があります。  
  
-   パス文字列を引用符で囲みます。  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   バック ティック文字 (') を使用して、かっこをエスケープします。  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   16 進数表記を使用して、かっこをエンコードします。  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a>参照  
 [PowerShell での SQL Server 識別子](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
