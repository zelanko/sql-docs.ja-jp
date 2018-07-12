---
title: パラメーターをコマンド |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2ae43260105acca3d638749d197e4e0d95a0260
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426831"
---
# <a name="command-parameters"></a>コマンドのパラメーター
  コマンド テキスト内のパラメーターは、疑問符文字でマークされます。 たとえば、次の SQL ステートメントでは 1 つの入力パラメーターがマークされています。  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 ネットワーク トラフィックを削減してパフォーマンスを向上させるために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーはない自動的にパラメーター情報を取得しない限り、 **icommandwithparameters::getparameterinfo**または**Icommandprepare::prepare**コマンドを実行する前に呼び出されます。 つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが自動的にしません。  
  
-   指定されたデータ型の正確性を検証**icommandwithparameters::setparameterinfo**します。  
  
-   アクセサー バインド情報で指定された DBTYPE から、そのパラメーターに対する適切な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にマップすること。  
  
 アプリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型のパラメーターと互換性のないデータ型を指定すると、上記のいずれかが原因で、エラーが発生したり、有効桁数が失われる可能性があります。  
  
 このようなことが起きないようにするには、アプリケーションで次の条件を満たす必要があります。  
  
-   いることを確認*して*と一致する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ハード コーディングする場合に、パラメーターのデータ型**icommandwithparameters::setparameterinfo**します。  
  
-   アクセサーをハードコーディングしている場合、パラメーターにバインドされている DBTYPE 値の型を、パラメーターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型と同じにします。  
  
-   呼び出すアプリケーションのコーディング**icommandwithparameters::getparameterinfo**プロバイダーが取得できるように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パラメーターのデータ型に動的にします。 これにより、ネットワーク上でサーバーとの余分なやり取りが増えることに注意してください。  
  
> [!NOTE]  
>  プロバイダーは呼び出しをサポートしていません**icommandwithparameters::getparameterinfo**は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]UPDATE または DELETE ステートメントの FROM 句では; を含むすべての SQL ステートメントはパラメーターを含むサブクエリによってSQL ステートメントなど、比較の両方の式内のパラメーター マーカーを格納しているか、定量化された述語。または、関数のパラメーターをパラメーターのいずれかをクエリします。 SQL ステートメントのバッチを処理するときに、プロバイダーもサポートしていません通話**icommandwithparameters::getparameterinfo**のバッチの最初のステートメントの後のステートメントでパラメーター マーカー。 コメント (/* \*/) では使用できません、[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンド。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、SQL ステートメント コマンドの入力パラメーターをサポートしています。 プロシージャ呼び出しコマンドで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、入力、出力、および入力/出力パラメーターをサポートしています。 出力パラメーターの値は、実行時 (行セットが返されない場合のみ)、または返されたすべての行セットがアプリケーションによって使用されたときにアプリケーションに返されます。 返される値が有効であることを確認するを使用して**IMultipleResults**行セットの使用量を強制的にします。  
  
 ストアド プロシージャ パラメーターの名前を DBPARAMBINDINFO 構造体で指定する必要はありません。 NULL の値を使用、 *pwszName*メンバーを示すために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがパラメーター名を無視しで指定された序数だけを使用する必要があります、 *rgParamOrdinals*のメンバー **icommandwithparameters::setparameterinfo**します。 コマンド テキストに名前付きのパラメーターと名前のないパラメーターの両方が含まれている場合、どの名前付きパラメーターよりも前に、名前のないパラメーターをすべて指定する必要があります。  
  
 ストアド プロシージャのパラメーターの名前が指定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが有効であることを確認する名前を確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、コンシューマーから不適切なパラメーター名を受信すると、エラーが返されます。  
  
> [!NOTE]  
>  サポートを公開する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XML とユーザー定義型 (UDT)、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを実装する新しい[ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)インターフェイス。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](commands.md)  
  
  
