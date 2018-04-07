---
title: パラメーターをコマンド |Microsoft ドキュメント
description: コマンドのパラメーター
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, parameters
- OLE DB Driver for SQL Server, commands
- parameters [OLE DB Driver for SQL Server], OLE DB
- commands [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9358369e5c6c5c57bc6000689f831a405d16e5d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="command-parameters"></a>コマンドのパラメーター
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  コマンド テキスト内のパラメーターは、疑問符文字でマークされます。 たとえば、次の SQL ステートメントでは 1 つの入力パラメーターがマークされています。  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 ネットワーク トラフィックを減らすことによってパフォーマンスを向上させる SQL Server の OLE DB Driver は自動的に派生していませんパラメーター情報しない限り、 **icommandwithparameters::getparameterinfo**または**ICommandPrepare:。準備**コマンドを実行する前に呼び出されます。 つまり、OLE DB Driver for SQL Server が自動的にしません。  
  
-   指定されたデータ型が正しいことを確認してください**icommandwithparameters::setparameterinfo**です。  
  
-   アクセサー バインド情報で指定された DBTYPE から、そのパラメーターに対する適切な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型にマップすること。  
  
 アプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型のパラメーターと互換性のないデータ型を指定すると、上記のいずれかが原因で、エラーが発生したり、有効桁数が失われる可能性があります。  
  
 このようなことが起きないようにするには、アプリケーションで次の条件を満たす必要があります。  
  
-   いることを確認*して*と一致する、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ パラメーターの型の場合はハード コーディング**icommandwithparameters::setparameterinfo**です。  
  
-   アクセサーをハードコーディングしている場合、パラメーターにバインドされている DBTYPE 値の型を、パラメーターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と同じにします。  
  
-   アプリケーションのコードを呼び出す**icommandwithparameters::getparameterinfo**プロバイダーを取得できるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]パラメーターのデータ型に動的にします。 これにより、ネットワーク上でサーバーとの余分なやり取りが増えることに注意してください。  
  
> [!NOTE]  
>  プロバイダーには、呼び出すことはできません**icommandwithparameters::getparameterinfo**のいずれか[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]UPDATE または DELETE ステートメントの FROM 句で指定を含むすべての SQL ステートメントのパラメーターを含むサブクエリに依存。SQL ステートメントのような比較の両方の式内のパラメーター マーカーを含むまたは定量化された述語です。または、クエリ関数のパラメーターをここでは、パラメーターのいずれか。 SQL ステートメントのバッチを処理するときに、プロバイダーも呼び出すことはできません**icommandwithparameters::getparameterinfo**バッチ内の最初のステートメントの後にあるステートメントのパラメーター マーカー。 コメント (/* \*/) では使用できません、[!INCLUDE[tsql](../../../includes/tsql-md.md)]コマンド。  
  
 SQL Server の OLE DB Driver は、SQL ステートメント コマンドで入力パラメーターをサポートします。 プロシージャ呼び出しコマンドには、SQL Server の OLE DB Driver は、入力、出力、および入力/出力パラメーターをサポートします。 出力パラメーターの値は、実行時 (行セットが返されない場合のみ)、または返されたすべての行セットがアプリケーションによって使用されたときにアプリケーションに返されます。 返される値が有効であることを確認するを使用して**IMultipleResults**行セットの消費量を強制的にします。  
  
 ストアド プロシージャ パラメーターの名前を DBPARAMBINDINFO 構造体で指定する必要はありません。 値として NULL を使用して、 *pwszName*メンバーを OLE DB Driver for SQL Server がパラメーター名を無視するで指定された序数だけを使用することを示す、 *rgParamOrdinals* のメンバー**Icommandwithparameters::setparameterinfo**です。 コマンド テキストに名前付きのパラメーターと名前のないパラメーターの両方が含まれている場合、どの名前付きパラメーターよりも前に、名前のないパラメーターをすべて指定する必要があります。  
  
 ストアド プロシージャのパラメーターの名前が指定されている場合、OLE DB Driver for SQL Server は有効であることを確認する名前を確認します。 SQL Server の OLE DB Driver は、コンシューマーから不適切なパラメーター名を受け取ると、エラーを返します。  
  
> [!NOTE]  
>  サポートを公開する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、OLE DB Driver for SQL Server を実装して、新しい XML およびユーザー定義型 (UDT)、 [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../oledb/ole-db-commands/commands.md)  
  
  
