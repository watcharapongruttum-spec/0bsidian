# Angular Lifecycle

- `ngOnInit`: Called after the component's initial view has been rendered.
- `ngOnChanges`: Called whenever an input property of the component changes.
- `ngOnDestroy`: Called before the component is destroyed.

**call-api.component.ts**
```ts
export class CallApiComponent implements OnInit {
  constructor(private http: HttpClient, private tripService: TripService) {}
  trips: TripGetResponse[] = [];

  ngOnInit(): void {
    this.loadDataAsync();
    console.log('Init State');    
  }

  async loadDataAsync (){
    this.trips = await this.tripService.getTrip();
  }
  ```

![[Pasted image 20231124080937.png]]