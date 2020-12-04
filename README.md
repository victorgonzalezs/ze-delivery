
<p>
    <mat-toolbar>
      <span>Cadastrados</span>
    </mat-toolbar>
  </p>
  
<mat-form-field>
    <mat-label>Filtro</mat-label>
    <input matInput (keyup)="applyFilter($event)" placeholder="Nome, Inscri&ccedil;&atilde;o, Status ou Data de Cadastro" #input>
  </mat-form-field>
  
  <div class="mat-elevation-z8">
    <table mat-table [dataSource]="dataSource" matSort>
  
      <ng-container matColumnDef="farol">
        <th mat-header-cell *matHeaderCellDef mat-sort-header>  </th>
        <td mat-cell *matCellDef="let row" [style.color]="row.farol_color"><mat-icon aria-hidden="false"> {{row.farol}}</mat-icon> </td>
      </ng-container>
  
      <ng-container matColumnDef="nome">
        <th mat-header-cell *matHeaderCellDef mat-sort-header> NOME </th>
        <td mat-cell *matCellDef="let row"> {{row.nome}} </td>
      </ng-container>
  
      <ng-container matColumnDef="inscricao">
        <th mat-header-cell *matHeaderCellDef mat-sort-header> INSCRI&Ccedil;&Atilde;O </th>
        <td mat-cell *matCellDef="let row"> {{row.inscricao}} </td>
      </ng-container>
  
      <ng-container matColumnDef="agentes">
        <th mat-header-cell *matHeaderCellDef mat-sort-header> AGENTES </th>
        <td mat-cell *matCellDef="let row" > {{row.agentes}} </td>
      </ng-container>

      
      <ng-container matColumnDef="status">
        <th mat-header-cell *matHeaderCellDef mat-sort-header> STATUS CLIENTE </th>
        <td mat-cell *matCellDef="let row"> {{row.status}} </td>
      </ng-container>
        
      <ng-container matColumnDef="data">
        <th mat-header-cell *matHeaderCellDef mat-sort-header> DATA CADASTRO </th>
        <td mat-cell *matCellDef="let row"> {{row.data}} </td>
      </ng-container>
  
      <tr mat-header-row *matHeaderRowDef="displayedColumns; sticky: true"></tr>
      <tr mat-row *matRowDef="let row; columns: displayedColumns;"></tr>
  
      <tr class="mat-row" *matNoDataRow>
        <td class="mat-cell" colspan="4">N&atilde;o existem dados para"{{input.value}}"</td>
      </tr>
    </table>
  
    <mat-paginator [pageSizeOptions]="[5, 10, 25, 100]"></mat-paginator>
    
  </div>
