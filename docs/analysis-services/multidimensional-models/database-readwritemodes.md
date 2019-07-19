---
title: データベースの Readwritemode |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e80433c224f08b9074a8d1ef93ef96bdc157853
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178847"
---
# <a name="database-readwritemodes"></a>データベースの ReadWriteMode
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者 (DBA) がデータベースを、読み書き可能から読み取り専用に変更したり、読み取り専用から読み書き可能に変更したりすることは少なくありません。 こうした状況は、ソリューションのスケールアウトやパフォーマンスの向上のために 1 つのデータベース フォルダーを複数のサーバー間で共有するなど、ビジネス上のニーズによって頻繁に発生します。 このような場合は、 **ReadWriteMode** データベース プロパティを使用すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DBA はデータベースの動作モードを容易に変更できます。  
  
## <a name="readwritemode-database-property"></a>ReadWriteMode データベース プロパティ  
 **ReadWriteMode** データベース プロパティは、データベースが読み取り/書き込みモードと読み取り専用モードのどちらであるかを指定します。 このプロパティの使用可能な値は 2 つだけです。 データベースが読み取り専用モードの場合は、変更または更新をデータベースに適用できません。 一方、データベースが読み取り/書き込みモードの場合は、変更や更新を行うことができます。 **ReadWriteMode** データベース プロパティは読み取り専用プロパティとして定義されています。このプロパティは、 **Attach** コマンドを使用してのみ設定できます。  
  
 データベースが読み取り専用モードの場合は、一定の制限が適用され、データベースに許可されている通常の操作に影響を与えます。 制限される操作については、次の表を参照してください。  
  
|ReadOnly モード|制限される操作|  
|-------------------|---------------------------|  
|XML/A コマンド<br /><br /> <br /><br /> 注:これらのコマンドのいずれかを実行するときに、エラーが発生します。|**作成**<br /><br /> **Alter**<br /><br /> **Del**<br /><br /> **プロセス**<br /><br /> **MergePartitions**<br /><br /> **DesignAggregations**<br /><br /> **CommitTransaction**<br /><br /> **復元**<br /><br /> **Synchronize**<br /><br /> **[挿入]**<br /><br /> **Update**<br /><br /> **Drop**<br /><br /> <br /><br /> 注:読み取り専用設定されているデータベースでは、セルの書き戻しを許可してください。ただし、変更がコミットすることはできません。|  
|MDX ステートメント<br /><br /> <br /><br /> 注:これらのステートメントのいずれかを実行するときに、エラーが発生します。|**COMMIT TRAN**<br /><br /> **CREATE SESSION CUBE**<br /><br /> **ALTER CUBE**<br /><br /> **ALTER DIMENSION**<br /><br /> **CREATE DIMENSION MEMBER**<br /><br /> **DROP DIMENSION MEMBER**<br /><br /> **ALTER DIMENSION**<br /><br /> <br /><br /> 注:Excel ユーザーはその機能を使用して内部的に実装されているため、ピボット テーブルのグループ化機能を使用できません**CREATE SESSION CUBE**コマンド。|  
|DMX ステートメント<br /><br /> <br /><br /> 注:これらのステートメントのいずれかを実行するときに、エラーが発生します。|**CREATE [SESSION] MINING STRUCTURE**<br /><br /> **ALTER MINING STRUCTURE**<br /><br /> **DROP MINING STRUCTURE**<br /><br /> **CREATE [SESSION] MINING MODEL**<br /><br /> **DROP MINING MODEL**<br /><br /> **IMPORT**<br /><br /> **SELECT INTO**<br /><br /> **INSERT**<br /><br /> **UPDATE**<br /><br /> **DELETE**|  
|バックグラウンド操作|データベースを変更するすべてのバックグラウンド処理は無効になっています。 これには、レイジー処理およびプロアクティブ キャッシュが含まれています。|  
  
## <a name="readwritemode-usage"></a>ReadWriteMode の使用方法  
 **ReadWriteMode** データベース プロパティは、 **Attach** データベース コマンドの一部として使用されます。 **Attach** コマンドを使うと、データベース プロパティに **ReadWrite** または **ReadOnly**を設定できます。 **ReadWriteMode** データベース プロパティの値は、読み取り専用として定義されているため、直接更新することはできません。 データベースは、 **ReadWriteMode** プロパティが **ReadWrite**に設定された状態で作成されます。 データベースを読み取り専用モードで作成することはできません。  
  
 **ReadWriteMode** データベース プロパティの **ReadWrite** と **ReadOnly**を切り替えるには、 **Detach/Attach** コマンド シーケンスを実行する必要があります。  
  
 **Attach**を除き、すべてのデータベース操作では、 **ReadWriteMode** データベース プロパティが現在の状態で維持されます。 たとえば、 **Alter**、 **Backup**、 **Restore**および **Synchronize** などの操作では、 **ReadWriteMode** 値が保持されます。  
  
> [!NOTE]  
>  ローカル キューブは、読み取り専用データベースから作成できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Analysis Services データベースのインポートとデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースの移動](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Detach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Attach 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
