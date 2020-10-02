const {restaurant} = require('./models')

describe("Restaurant tests", () =>{
    beforeAll((done)=>{
        
        db.run('CREATE TABLE restaurants(id INTEGER PRIMARY KEY, name TEXT, image TEXT);', done)
    })

    test('create a restaurant for the data row', async (done)=>{
        let restaurant=new Restaurant({name:"Tattu", image:"http://image.url"})

        db.get('SELECT*FROM restaurant WHERE id=1;', async(done) =>{
            const restaurant= await new Restaurant({name:"Tattu", image:"http://image.url"})
            expect(restaurant.id).toBe(1)
            expect(restaurant.name).toBe("Tattu")
            done()
        })
    })

    test('when a restaurant is created it is added to the database', async (done)=>{

        const restaurant = await new Restaurant({name:"Tattu", image:"http://image.url"})
        expect(restaurant.id).toBe(1)
    })
  
    test('create a menu and add it to the database', async(done) =>{

    })
})
