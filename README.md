<p>
    <mat-toolbar>
      <span>Pesquisa</span>
    </mat-toolbar>
  </p>
  <mat-form-field class="example-form-field">
    <mat-label>Pesquisar cliente</mat-label>
    <input matInput type="text" [(ngModel)]="value">
    <button mat-button *ngIf="value" matSuffix mat-icon-button aria-label="Clear" (click)="value=''">
      <mat-icon>close</mat-icon>
    </button>

  </mat-form-field>
  <button mat-raised-button>Pesquisar</button>
  <button mat-raised-button>Pré-cadastrar Lista</button>
